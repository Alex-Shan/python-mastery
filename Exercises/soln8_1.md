# 练习 8.1 — 解答

## (b) 为对象添加迭代功能

```python
# structure.py
...
        
class Structure(metaclass=StructureMeta):
    ...
    def __iter__(self):
        for name in self._fields:
            yield getattr(self, name)
    ...
```

## (c) 迭代的惊人能力

```python
# structure.py
...
        
class Structure(metaclass=StructureMeta):
    ...
    def __eq__(self, other):
        return isinstance(other, type(self)) and tuple(self) == tuple(other)
    ...
```

## (d) 监控流式数据源

```python
# follow.py
import os
import time

def follow(filename):
    '''
    Generator that produces a sequence of lines being written at the end of a file.
    '''
    with open(filename,'r') as f:
        f.seek(0,os.SEEK_END)
        while True:
             line = f.readline()
             if line == '':
                 time.sleep(0.1)    # Sleep briefly to avoid busy wait
                 continue
             yield line

# Example use
if __name__ == '__main__':
    for line in follow('Data/stocklog.csv'):
        row = line.split(',')
        name = row[0].strip('"')
        price = float(row[1])
        change = float(row[4])
        if change < 0:
            print('%10s %10.2f %10.2f' % (name, price, change))
```

**讨论**

这里使用 `time.sleep()`，是为了避免 CPU 忙等待，例如在等待新数据行时以 100% 的 CPU 占用率运行无限循环。



[返回](ex8_1.md)
