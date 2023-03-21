# Python Standard Library

## Introduction

standard library contains:

* language "core" - data types, syntactic properties, etc., but
  does not fully define semantics
* built-in functions and exceptions
* modules
  * both C modules compiled into Python interpreter and pure
    Python modules imported in source form
  * some highly highly Python-specific, like modules providing introspection
    functionality
  * some OS-specific
  * some only available when Python is compiled/installed with certain options

### Notes on Availability

* check out [Emscripten](https://emscripten.org/) and [WASI](https://wasi.dev/)
* check out [Pyodide](https://pyodide.org/) and [PyScript](https://pyscript.net/)
* basicaly, Emscriptan and WASI cannot provide everything that regular CPython
  provides; limitations concern:
  * process-related APIs: fork(), execve(), waitpid(), kill(), subprocess
  * different socket behavior ⟶ learn more!
  * some functions are just stubs (do nothing, return hardcoded values)
  * some file-related functionalities are not available

## Built-in Functions

* `abs` ✓
* `aiter` - async version of iter; same as `x.__aiter__()`
* `all` ✓
* `anext` - async variant of next
* `any` ✓
* `ascii` - `repr`, but escaped
* `bin` ✓
* `bool` ✓
* `breakpoint` - for debugging <!-- TODO: REVIEW  -->
* `bytearray` ✓
* `bytes` - just like `bytearrray`, but immutable
* `callable` ✓
* `chr` ✓
* `@classmethod` ✓
* `compile` - looks interesting, need to look into ⟶
* `complex` ✓
* `delattr` - equaivalent to `del x.foobar` ⟶
* `dict` ✓
* `dir` - "current local scope"
* `divmod` - `(a // b, a % b)` (quotient and remainder)
* `enumerate` ✓
* `eval` ✓ ⟶ takes optional globals and locals
* `exec` ✓ ⟶ when and how is it best used?
* `filter` ✓ ⟶ `itertools.filterfalse()` does the opposite
* `float` ✓
* `format` ⟶
* `frozenset` ⟶
* `getattr` - alternative to dot-indexing
* `globals` ⟶ need to experient with this
* `hasattr` ✓
* `hash` ✓
* `help` ✓
* `hex` ✓
* `id` ✓
* `input` ✓
* `int` ✓
* `isinstance` ✓
* `issubclass` ✓
* `iter` ⟶ learn about what `sentinel` does
* `len` ✓
* `list` ✓
* `locals` ✓
* `map` ✓
* `max` ✓
* `memoryview` ⟶
* `min` ✓
* `next` ✓
* `object` ✓
* `oct` ✓
* `open` ✓ ⟶
* `ord` ✓
* `pow` ✓
* `print` ✓
* `property` ⟶ good way to improve my Python code
* `range` ✓
* `repr` ✓
* `reversed` ✓
* `round` ✓
* `set` ✓
* `setattr` - essentially alternative attribute assignment
* `slice` ⟶
* `sorted` ✓
* `@staticmethod` ✓
* `str` ✓
* `sum` ✓
* `super` ⟶ review usage
* `tuple` ✓
* `type` ✓
* `vars` ⟶
* `zip` ✓
* `__import__` - advanced function not needed in everyday programming
