# Ex.05 Design a Website for Server Side Processing
# Date:05/12/24
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```

home.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Filament Power Calculator</title>
    <style>
        /* Global Styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }

        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }

        main {
            margin: 20px;
            text-align: center;
        }

        section.calculator {
            background-color: #fff;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
            width: 300px;
            text-align: left;
        }

        label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
        }

        input {
            margin-bottom: 10px;
            padding: 8px;
            width: calc(100% - 16px);
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            padding: 10px 20px;
            background-color: #333;
            color: #fff;
            border: none;
            cursor: pointer;
            border-radius: 4px;
            width: 100%;
            font-size: 1em;
            font-weight: bold;
        }

        button:hover {
            background-color: #555;
        }

        #result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
            padding: 10px;
            background-color: #e0e0e0;
            border-radius: 4px;
            text-align: center;
        }

        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <header>
        <h1>Lamp Filament Power Calculator</h1>
    </header>
    <main>
        <section class="calculator">
            <h2>Enter Values to Calculate Power</h2>
            <form action="{% url 'calculate_power' %}" method="post">
                {% csrf_token %}
                <label for="intensity">Intensity (I):</label>
                <input type="number" id="intensity" name="intensity" required>
                
                <label for="resistance">Resistance (R):</label>
                <input type="number" id="resistance" name="resistance" required>
                
                <button type="submit">Calculate Power</button>
            </form>
            <div id="result">
                {% if result %}
                    <strong>Power (P):</strong> {{ result }} watts
                {% endif %}
            </div>
        </section>
    </main>
    <footer>
        <p>&copy; Karthick.S </p>
    </footer>
</body>
</html>


urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
    path('calculate/', views.calculate_power, name='calculate_power'),
]

views.py

from django.shortcuts import render
from django.http import HttpResponse

def home(request):
    return render(request, 'calculator/home.html')

def calculate_power(request):
    if request.method == 'POST':
        intensity = float(request.POST.get('intensity'))
        resistance = float(request.POST.get('resistance'))
        power = (intensity ** 2) * resistance
        return render(request, 'calculator/home.html', {'result': power})
    return HttpResponse("Invalid request")
           
           
```
# SERVER SIDE PROCESSING:

![Screenshot 2024-12-12 194710](https://github.com/user-attachments/assets/7e995246-17d0-4c92-a8e1-51bb8e251801)

# HOMEPAGE:
![Screenshot 2024-12-05 145218](https://github.com/user-attachments/assets/07ea6ad2-3baa-482a-8df8-b0b793b21cc4)
![Screenshot 2024-12-05 145114](https://github.com/user-attachments/assets/4b2d19a9-1b9b-4b04-a328-2e5a6a56b7cc)


# RESULT:
The program for performing server side processing is completed successfully.
