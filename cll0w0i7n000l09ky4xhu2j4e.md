---
title: "Get User's Location, Country and Currency in Django"
seoTitle: "How To Get User's Location, Country and Currency in Django"
seoDescription: "This article shows you how to display currency symbol based on the user’s current location (country)."
datePublished: Fri Aug 04 2023 20:58:47 GMT+0000 (Coordinated Universal Time)
cuid: cll0w0i7n000l09ky4xhu2j4e
slug: user-location-country-and-currency-in-django
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691337376842/77214e21-b5ea-4110-b730-8a07fc435a35.jpeg
tags: json, django, geolocation

---

I once had to create a location-based ecommerce application with [Django Web Framework](https://www.djangoproject.com/) as the backend. While building the project, I needed a way to display products’ prices and currency based on the current user’s location. I made some research, got it working, then finally integrated it into the project.

This article shows you how to display currency symbol based on the user’s current location (country).

In this article, the following Frameworks and libraries will be used:

* Django
    
* GeoIP2
    

### Let’s Get Right Into It

#### Install a virtual Environment.

It is part of development best practices to create your project in a virtual environment. Use **venv** to install and activate a virtual environment named **env**:

```bash
python -m venv env

source env/bin/activate # Linux/MacOS
env\Scripts\activate.bat # Windows
```

#### Install Django and GeoIP

```bash
pip install Django
pip install geoip2
```

#### Create Django Project

```bash
django-admin startproject geolocation
```

#### Create Django App

```bash
python manage.py startapp currency
```

#### Install App

Open **settings.py** file and add the currency app to the list of installed app:

```bash
INSTALLED_APPS = [
    ...
    'currency',
]
```

#### Start Development Server

```bash
python manage.py runserver
```

Our development server is now running.

#### Get User’s Country

Open the **views.py** file located in the **currency** app and add the following code:

```python
from django.shortcuts import render
from django.contrib.gis.geoip2 import GeoIP2

def currency(request):
    g = GeoIP2()
    remote_addr = request.META.get('HTTP_X_FORWARDED_FOR')
    if remote_addr:
        address = remote_addr.split(',')[-1].strip()
    else:
        address = request.META.get('REMOTE_ADDR')
    country = g.country_code(address)
```

In the code above, I got the user’s IP address from the **request** object. The IP address is located in either **HTTP\_X\_FORWARDED\_FOR** or **REMOTE\_ADDR** in the request object

I then passed in the IP address  - as a parameter  - into GeoIP2’s **country\_code** method to get the user’s country.

#### Get the Country’s Currency

To get the currency of the country in which the user is, we will make use of a **JSON** (Javascript Object Notation) file which contains a list of countries, their country code, currency, currency symbol and other information.

This JSON file can be gotten [here](https://gist.github.com/portapipe/a28cd7a9f8aa3409af9171480efcc090). You can either download the JSON file and add it to your project or use the link.

Let’s take a look at the structure of this JSON file:

```json
[
    {
        "id": 154,
        "name": "Nigeria",
        "isoAlpha2": "NG",
        "isoAlpha3": "NGA",
        "isoNumeric": 566,
        "currency": {
        "code": "NGN",
        "name": "Naira",
        "symbol": "₦"
    },
]
```

Let’s parse this JSON file and extract the information we need from it.

Update your **views.py** file with the following:

```python
from django.shortcuts import render
from django.contrib.gis.geoip2 import GeoIP2
import json

def currency(request):
    g = GeoIP2()
    remote_addr = request.META.get('HTTP_X_FORWARDED_FOR')
    if remote_addr:
        address = remote_addr.split(',')[-1].strip()
    else:
        address = request.META.get('REMOTE_ADDR')
    country = g.country_code(address)

    with open('static/json/currency.json', encoding="utf8") as f:
        data = json.load(f)
        for keyval in data:
            if country == keyval['isoAlpha2']:
                code = keyval['currency']['code']
                symbol = keyval['currency']['symbol']
    return [code, symbol]
```

In this function, I:

* Open the JSON file.
    
* Loop through the dictionaries in the list.
    
* Search for any **isoAlpha2** key with the **country** variable as its value
    
* Get the currency key of the dictionary
    
* Return the **currency** values  - code and symbol -  in a list
    

With that out of the way, we can now create a view that makes use of this function.

In **views.py**, add the following view:

```python
from django.http import HttpResponse
...

def index(request):
    currency= {
        "currency_code": currency()[0],
        "currency_symbol": currency()[1]
    }
    return HttpResponse(currency)
```

#### Add URL Routes

Create a urls.py file in your app directory and add the following URL patterns:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='search'),
]
```

Update your project urls.py file:

```python
from django.urls import path, include

urlpatterns = [
    path('', include('currency.urls')),
]
```

Now, open your web browser and go to `https://127.0.0.1:8000` to see your current country's currency and symbol.

### Alternatives

Another alternative that we can use to get a user’s location is with **HTML Geolocation API**. This is a more accurate method of determining a user's coordinates.

Note that the users have to give you permission to access the location coordinates.

### CONCLUSION

In this article, we covered how to get a user’s location and country currency using Django. We also looked at how to parse and extract data from a JSON file.

Thanks for reading.

### REACH ME ON:

[GitHub](https://github.com/Dheelyte), [Twitter](https://twitter.com/DelightGbolahan), [LinkedIn](https://www.linkedin.com/in/delight-olagbuji)