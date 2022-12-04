# ORM

## Useful methods
1. `all`: Returns objects of a model
2. `filter`: filters a QuerySet base on a condition and returns QuerySet
3. `get`: returns an object, and it must be unique otherwise it will raise an exception, also if there isn't any user it will return `Model.DoesNotExist`
4. `exclude`: in opposite of filter, it will remove objects that satify a condition and it will return a QuerySet
5. `order_by`: Sorts objects
6. `count`: count QuerySet objects
7. `values`: It will return QuerySet objects as a dic
8. `values_list`: like `values` but instead of dict, it will returns an list, if we want just one field we can use `flat` param to make it a list, not a tuple

## Aggregation

```python
from django.db.models import *
from django.db.models import Avg, Sum, Max, Min
```
**Note: **we can use multiple aggregation functions

### AVG
By using this method, we can get the average of our desired property. By default, the return key will be `fieldname_avg`
```python
>>> User.objects.aggregate(Avg('score'))
{'score_avg' : 9.8}
``` 

If we want to determine the key, we can use `Avg` in this way:
```python
>>> User.objects.aggregate(avarage_score=Avg('score'))
{'average_score' : 9.8}
```

### Sum
Returns summation of objects:
```python 
>>> User.objects.aggregate(Sum('score'))
{'score__sum': 242}
>>> User.objects.aggregate(sum=Sum('score'))
{'sum': 242}
```

### Count
With this method, we can get the count of objects in a model
```python
>>> User.objects.aggregate(Count('score'))
{'score__count': 12}
>>> User.objects.aggregate(scores=Count('score'))
{'scores': 12}
```

### Max
As its name says, this method will return the greatest object in our objects
```python
>>> User.objects.aggregate(Max('score'))
{'score__max': 20}
>>> User.objects.aggregate(maximum=Max('score'))
{'maximum': 20}
```

### Min 
Opposite of `Max`!!!
```python
>>> User.objects.aggregate(Min('score'))
{'score__min': 2.25}
>>> User.objects.aggregate(minimum=Min('score'))
{'minimum': 2.25}
```

## F & Q
### F
If we want to compare an attribute in a model with another attribute in the same model, we can use the F object

```python
# Model
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=10)
    math_score = models.IntegerField()
    physics_score = models.IntegerField()

# Query
>>> from django.db.models import F
>>> Student.objects.filter(math_score__gt=F('physics_score'))
<QuerySet [...]>
```

We can use F and arithmetic expressions together

### Q
We can use this for logical operations like NOT, And, Or
```python
>>> conditions = Q(math_score__gte=10) | Q(physics_score__gte=10)
>>> Student.objects.filter(conditions)
<QuerySet [...]>
```

| Operation | Sign |
| --------- | ---- |
| AND | & |
| Order | \| |
| NOT | ~ |

## Manager
Django, by default, uses a manager called `objects`. We can change that name like below:

```python
class Books(models.Model):
    price = models.PositiveIntegerField(default=1000)
    books = models.Manager()
```

Then if we try to use `objects`, we will get an `AttributeError`, and we must use our specific name (`books`) instead of `objects`.

