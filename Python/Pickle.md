
Pickle is a library used to serialize objects via the `__reduce__` method, which should indicate the class + the parameters to pass to the `__init__`of this class
`

```
MyClass:
	def __init__(self, i: int):
		self._i = i
	def __reduce__(self):
		return (self.__cls__, (i,))
```

If now the `__reduce__` would be returning `(os.system, ("ls -la",))`, this would be called when deserializing the object.