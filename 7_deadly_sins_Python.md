# 7 Deadly Sins in Python

There has been a lot written about common Python mistakes (not only) beginners do. It is natural to do mistakes and thus shall not be considered a priori as a sin.

However, some of those mistakes (bugs) do not raise an exception or misbehaviour does not occur right away, even though syntactically correct. Finding this kind of bugs may result in a long and intimidating debugging session and excessive caffein beverage consumption. Therefore I call these "hidden" bugs deadly sins.

## 1) Except-pass

Using `pass` in exception handling without any real exception handling is the deadly sin number one, since any error is completely ignored and thus extremly hardly located. In very well justified occasions, Except-pass construction with comment explaining why this is fine may be used. Sinners shall rot in the same circle of hell as child molesters and people who speak in the cinema.
  ```python
  except:
    pass
  ```

## 2) Monkey patching

Whenever you are monkey patching, it is just a matter of time, until you end up with a monkey scratching your eyes from behind. Since Python allows it (praise the dynamical typing), the temptation is even larger.

## 3) Misusing globals

TODO

## 4) Importing all

TODO

```python
from module import *
```

## 5) Using mutables ad default

TODO

## 6) My script is for a one-time use

We've all been there. Not true and definitely not justified, since good habbits and proper tools can do miracules in basically no time.

## 7) Editing a list while iterating through it

TODO

> Note: Of course, every rule has it's exception. But these have very little of them and as we are all just a mortals... :-)
