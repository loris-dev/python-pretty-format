> This example provides a pretty format for objects, written in python.

```python

class Foo:
    def __init__(self, bar: str) -> None:
        self.bar = bar

    def __str__(self) -> str:
        return "{}({})".format(
            type(self).__name__,
            ", ".join(
                f"{key}={str(value)}"
                for key, value in self.__dict__.items()
                if not key.startswith("_")
            ),
        )

    __repr__ = __str__


foo = Foo('This is an example') # Object creation
print(foo) # Result: Foo(bar='This is an example')
print(repr(foo)) # Result: Foo(bar='This is an example')
