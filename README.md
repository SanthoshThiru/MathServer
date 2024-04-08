# Ex.05 Design a Website for Server Side Processing
## Date:08-04-2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
math.html

<html>
<head> 
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
        background-color: rgb(8, 54, 95);
        font-family: Arial, sans-serif;
    }
    .edge {
        width: 100%;
        text-align: center;
        padding-top: 50px;
    }
    .box {
        display: inline-block;
        border: thick dashed rgb(4, 23, 9);
        width: 500px;
        min-height: 300px;
        font-size: 20px;
        background-color: rgb(122, 218, 233);
        padding: 20px;
    }
    .formelt {
        color: black;
        text-align: center;
        margin-top: 10px;
        margin-bottom: 10px;
    }
    h1, h3 {
        color: rgb(32, 2, 43);
    }</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Surface Area of Right Cylinder</h1>
        <h3>SANTHOSH T (212223220100)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfaceareaofcylinder/',views.surfacearea,name="surfaceareaofcylinder"),
    path('',views.surfacearea,name="surfaceareaofcylinderroot")
]

views.py

from django.shortcuts import render

def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    
    if request.method == 'POST':
        print("POST method is used")
        
        print('request=', request.POST)
        
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html', context)

```
## SERVER SIDE PROCESSING:
![alt text](<webssp/mathapp/templates/mathapp/Screenshot 2024-04-08 133235.png>)

## HOMEPAGE:
![alt text](<webssp/mathapp/templates/mathapp/Screenshot 2024-04-08 133213.png>)

## RESULT:
The program for performing server side processing is completed successfully.
