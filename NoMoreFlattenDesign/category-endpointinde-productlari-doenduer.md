# 6️⃣ Category endpointinde productları döndür

## Görev:

* _<mark style="color:purple;">Category</mark>_ için özel bir _<mark style="color:orange;">product\_serializer</mark>_ yaz
* _<mark style="color:orange;">category\_serializer'</mark>_a yazdığın _<mark style="color:orange;">product\_serializer'</mark>_ı koy
  * Böylece _<mark style="color:purple;">Category</mark>_ endpointinde **kategoriye ait productları döndür.**

### Endpoint:

`http://127.0.0.1:8000/stock/categories/`

### Öncesi:



### Sonrası:

```json
[
    {
        "id": 1,
        "name": "Clothing",
        "product_count": 2,
        "products": [
            {
                "id": 1,
                "created": "2024-03-18T13:30:21.992575Z",
                "updated": "2024-03-18T13:31:32.189458Z",
                "name": "flex",
                "stock": 2,
                "category": 1,
                "brand": 1
            }
        ]
    }
]
```

{% code title="stock/serializers.py" %}
```python
class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = '__all__'

class CategorySerializer(serializers.ModelSerializer):
    product_count = serializers.SerializerMethodField()
    products = ProductSerializer(many=True, read_only=True)
    class Meta:
        model = Category
        fields = ['id', 'name', 'product_count', 'products']
#..
```
{% endcode %}

## Başlangıç noktası

`git clone git@github.com:snahmd/NoMoreFlattenDesign.git`

`git checkout 66fb8cb2e602e7ee54d3f90539f69667082b5225`

***

## Yapılanlar:



***

## Sonuç:
