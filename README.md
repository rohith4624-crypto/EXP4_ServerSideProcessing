# Ex.04 Design a Website for Server Side Processing
## Date:

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
```
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Interest Calculator</title>
    <style>
        {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    width: 400px;
    padding: 70px;
    background: white;
    box-shadow: 0px 4px 6px black;
    border-radius: 8px;
    text-align: center;
}

h1 {
    margin-bottom: 20px;
    font-size: 1.5em;
    color: rgb(58, 58, 58);
}

form {
    display: flex;
    flex-direction: column;
}

.form-group {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9em;
    color: rgb(58, 58, 58);
}

input {
    width: 100%;
    padding: 10px;
    font-size: 1em;
    border: 1px solid white;
    border-radius: 5px;
}

input#result {
    background-color: white;
    cursor: not-allowed;
}

button {
    width: 106%;
    padding: 10px;
    background-color: rgb(0, 123, 255);
    color: white;
    font-size: 1em;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color:rgb(0, 86, 179);
}
    </style>
</head>
<body>
    <div class="container">
        <h1>Simple Interest Calculator</h1>
        <form method="POST">
            {% csrf_token %}
            <label for="principal">Principal Amount (P):</label>
            <input type="number" id="principal" name="principal" required>

            <label for="rate">Rate of Interest (R):</label>
            <input type="number" id="rate" name="rate" required>

            <label for="time">Time (T in years):</label>
            <input type="number" id="time" name="time" required><br>

            <button type="submit">Calculate</button>
        </form>

        {% if simple_interest is not None %}
        <div class="result">
            <h2>Result:</h2>
            <p>Simple Interest: {{ simple_interest }}</p>
        </div>
        {% endif %}
    </div>
</body>
</html>

views.py
from django.shortcuts import render

def simple_interest_calculator(request):
    simple_interest = None
    if request.method == 'POST':
    
        principal = float(request.POST.get('principal', 0))
        rate = float(request.POST.get('rate', 0))
        time = float(request.POST.get('time', 0))

        simple_interest = (principal * rate * time) / 100

    return render(request, 'simple_interest.html', {'simple_interest': simple_interest})

urls.py
from django.contrib import admin
from django.urls import path
from formula import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('simplei/', views.simple_interest_calculator, name='simple_interest_calculator'),
]

```

## SERVER SIDE PROCESSING:

![serverside](https://github.com/user-attachments/assets/0ad364b1-0647-4358-8e8b-e32713978d63)

## HOMEPAGE:

![homepage](https://github.com/user-attachments/assets/130a29fb-6561-44ab-bf37-0c5e1dcb8825)

## RESULT:
The program for performing server side processing is completed successfully.
