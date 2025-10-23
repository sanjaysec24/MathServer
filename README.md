# Ex.05 Design a Website for Server Side Processing
## Date:23-10-2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
'''
math.html :

<html lang="en">
<head>
    <style>
        .Calculate {
            width: 30%;
            padding: 20px;
            margin: auto;
            background-color: rgb(25, 141, 180);
            text-align: center;
            border-radius:20px;
        }
        label {
            font-size: 20px;
        }
        p {
            font-size: 20px;
            font-weight: bold;
        }
        h1 {
            text-align: center;
        }
        input, button {
            padding: 10px;
            margin: 10px 0;
        }
        button {
            background-color:rgb(129, 137, 14);
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 10px;

        }
    </style>
    <title>Document</title>
</head>
<body>
    <h1>Calculating Power of a Lamp</h1>
    <div class="Calculate">
        <form action="{% url 'home' %}" method="post">
            {% csrf_token %}
            <label>Intensity:</label><br>
            <input type="text" name="intensity-input"><br>

            <label>Resistance:</label><br>
            <input type="text" name="resistance-input"><br>

            <button type="submit">Calculate</button>

            <p>The power of the lamp is: {{ output }}</p>
        </form>
    </div>
</body>
</html>

views.py

from django.shortcuts import render
def power(request):
    if request.method=='POST':
        intesity_value=int(request.POST.get('intensity-input'))
        resistance_value=int(request.POST.get('resistance-input'))
        power = (intesity_value ** 2) * resistance_value
        return render(request, 'mathapp/math.html',{'output':power})
    return render (request, 'mathapp/math.html')

urls.py:

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    #path("admin/", admin.site.urls),
    path('',views.power,name='home')
]
'''
## SERVER SIDE PROCESSING:

![alt text](<Screenshot 2025-10-23 135110.png>)
## HOMEPAGE:
![alt text](<Screenshot 2025-10-23 135027.png>)

## RESULT:
The program for performing server side processing is completed successfully.
