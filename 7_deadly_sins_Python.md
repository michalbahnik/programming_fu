# 7 Deadly Sins in Python

There has been a lot written about common Python mistakes (not only) beginners do. It is natural to do mistakes and thus shall not be considered a priori as a sin.

However, some of those mistakes (bugs) do not raise an exception or misbehaviour does not occur right away, even though syntactically correct. Finding this kind of bugs may result in a long and intimidating debugging session and excessive caffein beverage consumption. Therefore I call these "hidden" bugs deadly sins.

## 1) Except-pass

Using `pass` in exception handling without any real exception handling is the deadly sin number one, since any error is completely ignored and thus extremly hardly located. In very well justified occasions, Except-pass construction with comment explaining why this is fine may be used. Sinners shall rot in the same circle of hell as child molesters and people who speak in the cinema.
  ```python
  except:
    pass
  ```

## 2) Appending to system path

Whenever one writes something like
```python
sys.path.append(project_root)
```
a kitty dies. Please, turn your modules into nice packages.

## 3) Misusing globals

Globals are rarely really needed and hard to keep control of. They can be accessed from different parts of code and proper handling of access mostly doesn't worth the effort.

## 4) Importing all

Beside of cluttering up the workspace with many unused objects and possible slow-down on importing, this can replace existing symbols (objects, classes, functions,...)  without any notice.

```python
from module import *
```

## 5) Using mutables as default

This one can be quite unintuitive for beginners, but can cause a lot of debugging effort.

```python
def func(input: list = []):
    ...
```

## 6) Shadowing imports

```python
import time

time = time.now()
time_diff = time - time.now(). # error
```

This example is trivial to spot, however shadowing imports may be well hidden quite tricky to debug. So in general, descriptive and not too general names are a good best practice. Especially when using atandard libraries.

## 7) Using (Jupyter) notebooks for serious development

Jupyter notebooks are great for making tutorials, showcases or demonstrations, but not for a serious code.

> Note: Of course, every rule has it's exception. But these have very little of them and as we are all just a mortals... :-)
