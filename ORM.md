# ORM

## Useful methods
1. `all`: returns all objects of a model
2. `filter`: filters a QuerySet base on a condition and return QuerySet
3. `get`: returns an object and it must be unique otherwise it will raise an exception, also if there isn't any user it will return Model.DoesNotExist
4. `exclude`: in opposite of filter it will remove objects that satify a condition and it will return a QuerySet
5. `order_by`: Sorts objects
6. `count`: count QuerySet objects
7. `values`: It will return QuerySet objects as a dic
8. `values_list`: like `values` but instead of dic, it will returns an list, if we want just one field we can use `flat` param to make it as list not tuple

