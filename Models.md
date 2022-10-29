# Models

## Most Common Fields
| name | description |
| ----- | ----------|
| BinaryField | saves binary values|
| BooleanField | Saves boolean |
| CharField | Saves string (data type probabily will be varchar) |
| DateField | Saves Date |
| EmailField | Saves Emails |
| DateTimeField | Saves Date and Time |
| IntegerField | Saves int |
| FloatField | Save Float valus |
| TextField | Saves Strings (data type probabily will be text)| 

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
