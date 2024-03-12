# 🔍 Search and Filter

## Start Right Here

`git clone git@github.com:snahmd/NoMoreFlattenDesign.git`

`git checkout 5b0692c4b16f18ac66193bc94074344a8ee2da56`

***

## <mark style="background-color:green;">Search  Özelligi</mark>

Amacimiz endpointe search özelligi eklemek.

### Arama özellikli url: <a href="#arama-oezellikli-url" id="arama-oezellikli-url"></a>

`http://127.0.0.1:8000/stock/categories/?search=Cl`

***

Arama özelliği için viewsete iki tane şey eklemeliyiz.



{% code title="stock/views.py" %}
```python
from rest_framework import viewsets, filters
# ... [imports]

class CategoryViewSet(viewsets.ModelViewSet):
    # ... 
    filter_backends = [filters.SearchFilter]
    search_fields = ['name']
```
{% endcode %}



***

## <mark style="background-color:green;">Filter</mark>

#### Enpoint: <a href="#enpoint" id="enpoint"></a>

`http://127.0.0.1:8000/stock/categories/?name=Clothing`

[![Logo](https://www.django-rest-framework.org/img/favicon.ico)Filtering - Django REST framework](https://www.django-rest-framework.org/api-guide/filtering/#djangofilterbackend)

`pip install django-filter`

```python
INSTALLED_APPS = [
    ...
    'django_filters',
    ...
]
```

```python
from django_filters.rest_framework import DjangoFilterBackend

class CategoryViewSet(viewsets.ModelViewSet):
    # ...
    filter_backends = [filters.SearchFilter, DjangoFilterBackend]
    filterset_fields = ['name']
```
