# ⌨️ Calculate Product Count

## Start Right Here

`git clone git@github.com:snahmd/NoMoreFlattenDesign.git`

`git checkout e619fa8cae495a238c936fc7571333acf538a402`



***

## <mark style="color:red;background-color:purple;">**end point:**</mark> `http://127.0.0.1:8000/stock/categories/`

## <mark style="background-color:orange;">Bevor:</mark>

```json
[
    {
        "id": 1,
        "name": "Clothing"
    }
]
```

Update serializers.py

{% code title="stock/serializers.py" %}
```python
from rest_framework import serializers
from .models import Category, Brand, Product, Firm, Purchases, Sales

class CategorySerializer(serializers.ModelSerializer):
    product_count = serializers.SerializerMethodField()
    class Meta:
        model = Category
        fields = '__all__'

    def get_product_count(self, obj):
        return Product.objects.filter(category_id=obj.id).count()
```
{% endcode %}

## <mark style="background-color:orange;">Nach:</mark>

```json
[
    {
        "id": 1,
        "product_count": 0,
        "name": "Clothing"
    }
]
```
