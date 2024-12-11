# Ex.05 Design a Website for Server Side Processing
## Date: 11.12.2024

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
math.html

<!DOCTYPE html>
<html>

<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>POWER OF LAMP IN INCANDESCENT BULB</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
</head>

<body>
    <h1>POWER OF LAMP IN INCANDESCENT BULB</h1>
    <form method="POST">
        <div>
            INTENSITY: <input type="text" name="Intensity">(in A)<br>
        </div>
        <div>
            RESISTANCE: <input type="text" name="Resistence">(in Ω)<br>
        </div>
        <div>
            <input type="submit" value="Calculate"><br>
        </div>
        <div>
            POWER: <input type="text" name="Power">W<br>
        </div>
    </form>
</body>

</html>

views.py

from django.shortcuts import render

def powerlamp(request):
    context={}
    context['Power'] = ""
    context['I'] = ""
    context['R'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['I'] = I
        context['R'] = R
        print('Power=',Power)
    return render(request,'mathapp/math.html',context)

    urls.py

    from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('PowerOfLampFilamentInAnIncandescentBulb/',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb"),
    path('',views.powerlamp,name="PowerOfLampFilamentInAnIncandescentBulb"),
]
```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-12-11 200053.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-12-11 195305.png>)

## RESULT:
The program for performing server side processing is completed successfully.
