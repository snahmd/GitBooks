# 📢 Create First EndPoint

## Start Right Here

`git clone git@github.com:snahmd/NoMoreFlattenDesign.git`

`git checkout cfbd2abbc1e8bb6fe3c72fe0f546305bbfdf4c82`

***



{% tabs %}
{% tab title="Deutsch" %}
Zuerst erstellen wir den Serialisierer. Dieser hilft dabei, die vom Client kommenden Informationen in unseren Code zu konvertieren. Dann verwenden wir ihn in der Ansicht. Und schließlich erstellen wir unseren Endpunkt in der Url.
{% endtab %}

{% tab title="Turkce" %}
Ilk olarak serializer'i olusturuyoruz. Bu client tarafindan gelen bilgilerin bizim code muza donüstürülmesine yardimci. Sonra view'da bunu kullaniyoruz. Ve en son olarak url de endpoint'imizi olusturuyoruz.
{% endtab %}
{% endtabs %}

{% code title="stock/serializers.py" %}
```python
from rest_framework import serializers
from .models import Category, Brand, Product, Firm, Purchases, Sales    

class CategorySerializer(serializers.ModelSerializer):
    class Meta:
        model = Category
        fields = '__all__'

```
{% endcode %}

{% code title="stock/views.py" %}
```python
from django.shortcuts import render
from rest_framework import viewsets
from .models import Category, Brand, Product, Firm, Purchases, Sales
from .serializers import CategorySerializer

# Create your views here.

class CategoryViewSet(viewsets.ModelViewSet):
    queryset = Category.objects.all()
    serializer_class = CategorySerializer

```
{% endcode %}

{% code title="stock/urls.py" %}
```python
from django.urls import path, include
from rest_framework import routers
from .views import CategoryViewSet

router = routers.DefaultRouter()
router.register('categories', CategoryViewSet)

urlpatterns = [
    path('', include(router.urls)),
]
```
{% endcode %}

{% tabs %}
{% tab title="Deutsch" %}
Dann geben wir in der Datei admin.py an, dass sie im Verwaltungsbereich angezeigt werden soll, und fügen eine neue Kategorie im Verwaltungsbereich hinzu. Jeder sieht unsere Kategorien in unserem Endpunkt.
{% endtab %}

{% tab title="Türkce" %}
Sonra admin panelde göstermek icin admin.py dosyasinda belirtiyoruz ve adminden yeni category ekliyoruz. Endpointimizde herkes bizim categorylerimizi görüyor suan da.
{% endtab %}
{% endtabs %}

{% code title="stock/admin.py" %}
```python
from django.contrib import admin
from .models import Category, Brand, Product, Firm, Purchases, Sales
# Register your models here.

admin.site.register(Category)
#...
```
{% endcode %}
