# URLs

## URL Convetors:
1. `str`: It matches with any limited string except those ones with `/`, if you don't provide any url convertor, this is the default convertor.
2. `int`: It matches any positive integer number and pass the value to view function as `int`
3. `slug`: It matches any string containing ASCII, numbers, _ and -
4. `uuid`: An object of uuid.UUID will be given, you can refer [here](https://docs.python.org/3/library/uuid.html#uuid.UUID) to remove more.
5. `path`: like `str` but it can contains `/`

We usually use `str` and `int` and maybe `slug`!

