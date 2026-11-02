# 练习 7.2 — 解答

## (a) 复制元数据

```python
# logcall.py

from functools import wraps

def logged(func):
    print('Adding logging to', func.__name__)
    @wraps(func)
    def wrapper(*args,**kwargs):
        print('Calling', func.__name__)
        return func(*args,**kwargs)
    return wrapper
```

## (b) 带参数的装饰器

```python
# logcall.py

from functools import wraps
...
def logformat(fmt):
    def logged(func):
        print('Adding logging to', func.__name__)
        @wraps(func)
        def wrapper(*args, **kwargs):
            print(fmt.format(func=func))
            return func(*args, **kwargs)
        return wrapper
    return logged
```

之前的 `@logged` 可以重写为：

```python
logged = logformat('Calling {func.__name__}')
```

## (c) 装饰器与方法

交换装饰器顺序就可以使代码运行。例如：

```python
from logcall import logged

class Spam:
    @logged
    def instance_method(self):
        pass

    @classmethod
    @logged
    def class_method(cls):
        pass

    @staticmethod
    @logged
    def static_method():
        pass

    @property
    @logged
    def property_method(self):
        pass
```

思考为什么原来的顺序不起作用。能否让 `@logged` 无论按什么顺序应用都能正常工作？

## (d) 再谈验证

```python
# validate.py
...

from inspect import signature
from functools import wraps

def validated(func):
    sig = signature(func)

    # Gather the function annotations
    annotations = dict(func.__annotations__)

    # Get the return annotation (if any)
    retcheck = annotations.pop('return', None)

    @wraps(func)
    def wrapper(*args, **kwargs):
        bound = sig.bind(*args, **kwargs)
        errors = []

        # Enforce argument checks
        for name, validator in annotations.items():
            try:
                validator.check(bound.arguments[name])
            except Exception as e:
                errors.append(f'    {name}: {e}')

        if errors:
            raise TypeError('Bad Arguments\n' + '\n'.join(errors))

        result = func(*args, **kwargs)

        # Enforce return check (if any)
        if retcheck:
            try:
                retcheck.check(result)
            except Exception as e:
                raise TypeError(f'Bad return: {e}') from None
        return result

    return wrapper

def enforce(**annotations):
    retcheck = annotations.pop('return_', None)

    def decorate(func):
        sig = signature(func)

        @wraps(func)
        def wrapper(*args, **kwargs):
            bound = sig.bind(*args, **kwargs)
            errors = []

            # Enforce argument checks
            for name, validator in annotations.items():
                try:
                    validator.check(bound.arguments[name])
                except Exception as e:
                    errors.append(f'    {name}: {e}')

            if errors:
                raise TypeError('Bad Arguments\n' + '\n'.join(errors))

            result = func(*args, **kwargs)

            if retcheck:
                try:
                    retcheck.check(result)
                except Exception as e:
                    raise TypeError(f'Bad return: {e}') from None
            return result
        return wrapper
    return decorate
```




[返回](ex7_2.md)
