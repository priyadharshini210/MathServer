# Ex.05 Design a Website for Server Side Processing
## Date: 03/04/2024

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
math.html
```
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>AREA OF RECTANGLE</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body 
{
background-color:gray;
}
.edge {
width: 1440px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 500px;
}
.box {
display:block;
border: Thick dashed aquamarine;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color:beige;
}
.formelt{
color:rgb(255,0,179);
text-align: center;
margin-top: 7px;
margin-bottom: 6px;
}
h1
{
color:rgb(255, 0, 179);
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>AREA OF A RECTANGLE</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Base edge : <input type="text" name="length" value="{{l}}"></input>(in m)<br/>
</div>
<div class="formelt">
Height : <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>
```
views.py
```
from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'mathapp/math.html',context)
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```


## SERVER SIDE PROCESSING:
![Screenshot (12)](https://github.com/priyadharshini210/MathServer/assets/148514638/b5339b05-bc8a-47a1-b6b7-6ac22493e09d)

## HOMEPAGE:
![Screenshot (13)](https://github.com/priyadharshini210/MathServer/assets/148514638/f074d6ab-28e6-435c-9a3c-22c6f7c728c9)

## RESULT:
The program for performing server side processing is completed successfully.
