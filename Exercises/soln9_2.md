# 练习 9.2 — 解答

## (a) 创建包

无需修改太多源代码，只需创建以下目录结构：

```
structly/
    __init__.py
    validate.py
    reader.py
    structure.py
    tableformat.py
```

`__init__.py` 可以为空。只需稍微修改 `structure.py`，使导入语句正常工作。

```python
# structure.py

...
from .validate import Validator
```



[返回](ex9_2.md)
