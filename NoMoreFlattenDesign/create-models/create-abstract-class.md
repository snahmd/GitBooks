# 📭 Create Abstract Class

## Start From Here

`git clone git@github.com:snahmd/NoMoreFlattenDesign.git`

`git checkout c6bc1127b007791bdbbb9f623fa84816005bee44`

***

## Abstract Class

Wir sammeln die gemeinsamen Felder, die in den Modellen erstellt werden, in einer separaten Klasse, von der andere Klassen erben können. Das hilft uns, einen saubereren Code zu schreiben.

{% code title="stock/models.py" %}
```python
# ..


class UpdateCreate(models.Model):
    created = models.DateTimeField(auto_now_add=True)
    updated = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True
    
class Product(UpdateCreate):
    # ...
    
class Firm(UpdateCreate):
    # ...
    
class Purchases(UpdateCreate):
    # ...
    
class Sales(UpdateCreate):
    # ...

```
{% endcode %}
