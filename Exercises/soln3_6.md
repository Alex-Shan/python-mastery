# 练习 3.6 — 解答

## (a) 改善对象的输出表示

```python
# stock.py

class Stock:
    ...

    def __repr__(self):
        # Note: The !r format code produces the repr() string
        return f'{type(self).__name__}({self.name!r}, {self.shares!r}, {self.price!r})'
    ...
```

## (b) 使对象可比较

```python
class Stock:
    ...
    def __eq__(self, other):
        return isinstance(other, Stock) and ((self.name, self.shares, self.price) ==
                                 (other.name, other.shares, other.price))
    ...
```

## (c) 上下文管理器

练习中已给出代码。



[返回](ex3_6.md)
