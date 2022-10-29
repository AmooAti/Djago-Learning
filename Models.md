# Models

## Most Common Fields
| name          | description                                        |
| ------------- | -------------------------------------------------- |
| BinaryField   | saves binary values                                |
| BooleanField  | Saves boolean                                      |
| CharField     | Saves string (data type probabily will be varchar) |
| DateField     | Saves Date                                         |
| EmailField    | Saves Emails                                       |
| DateTimeField | Saves Date and Time                                |
| IntegerField  | Saves int                                          |
| FloatField    | Save Float valus                                   |
| TextField     | Saves Strings (data type probabily will be text)   |

**Q**: what about blob, decimal?

**Q**: Does date and datetiem field save values as timestamp? also what is the timestamp field?

**TODO**: Check all fields and complete datatypes in all dbs

## Fields parameters 

| param | values | description |
| ----- | ------ | ----------- |
| null | Boolean (True, False) | make field nullable |
|blank| Boolean (True,False)|field can be empty|
|default| any value | if we don't give field a value this default value will be used|
|choices| usually tuple | with this parameter we can assign a acceptable group of values that this field will accepts the tuple will have a sub tuple with value and label but we can use both of them in our code|


### Difference between blank and null
For example if field type is CharField, in that case if we use blank=True this field will have `""` in case of empty but if we make it nullable then the field value can be null



## Relations
### One-to-Many/Many-to-One

 ```python
from django.db import models


class User(models.Model):
    username = models.CharField(max_length=10)
    email = models.EmailField()
    signing_date = models.DateTimeField()
    

class Post(models.Model):
    content = models.TextField()
    writer = models.ForeignKey(User, on_delete=models.CASCADE)
 ```

 ### Many-to-Many
 ```python
from django.db import models

class User(models.Model):
    username = models.CharField(max_length=10)
    email = models.EmailField()
    signing_date = models.DateTimeField()

class Post(models.Model):
    content = models.TextField()
    writers = models.ManyToManyField(User)
 ```

 ### One-to-One
 ```python
 from django.db import models

class User(models.Model):
    username = models.CharField(max_length=10)
    email = models.EmailField()
    signing_date = models.DateTimeField()

class Post(models.Model):
    content = models.TextField()
    writers = models.OneToOneField(User)
 ```

 ## Reverse Relations 
 Assume that we have this relationsship:
 ```python
class Author(models.Model):
    name = models.CharField(max_length=20)

class Book(models.Model):
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
 ```

We can access books from Author obj like this:

```python
robert_martin.book_set.all()
``` 

accually we add _set to related_name of relation of the other obj and we can change related_name like this:
```python
class Book(models.Model):
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name='books')
```

and then it will be like this:
```python
robert_martin.books.all()
```

## Add and Remove objects
1. `create` method: It creates an object from model and saves it into database
   ```python
    User.objects.create(name="user")
   ```
2. `save` method: This method save changes of a model obj into database
   ```python
    user = User(name="user")
    user.save()
   ```
3. `delete` method: This method deletes an object from database
    ```python
    user = User(name="user")
    user.save()
    user.delete()
    ```