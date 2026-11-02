# 练习 9.3 — 解答

## (a) 控制导出符号

```python
# structure.py

__all__ = ['Structure']
...
```

```python
# reader.py

__all__ = [ 'read_csv_as_dicts',
            'read_csv_as_instances' ]
...
```

```python
# tableformat.py

__all__ = ['create_formatter', 'print_table']
...
```

## (b) 导出所有内容

```python
# structly/__init__.py

from .structure import *
from .reader import *
from .tableformat import *

__all__ = [ *structure.__all__,
	    *reader.__all__,
	    *tableformat.__all__ ]
```

## (c) 拆分模块

这包含几个部分。首先，`tableformat/formats` 中的各个文件如下：

```python
# tableformat/formats/text.py
from ..formatter import TableFormatter

class TextTableFormatter(TableFormatter):
    ...


# tableformat/formats/csv.py
from ..formatter import TableFormatter
class CSVTableFormatter(TableFormatter):
    ...


# tableformat/formats/html.py
from ..formatter import TableFormatter
class HTMLTableFormatter(TableFormatter):
    ...
```

`formatter.py` 如下：

```python
# tableformat/formatter.py

from abc import ABC, abstractmethod

def print_table(records, fields, formatter):
    if not isinstance(formatter, TableFormatter):
        raise RuntimeError('Expected a TableFormatter')

    formatter.headings(fields)
    for r in records:
        rowdata = [getattr(r, fieldname) for fieldname in fields]
        formatter.row(rowdata)

class TableFormatter(ABC):
    @abstractmethod
    def headings(self, headers):
        pass

    @abstractmethod
    def row(self, rowdata):
        pass

from .formats.text import TextTableFormatter
from .formats.csv import CSVTableFormatter
from .formats.html import HTMLTableFormatter

class ColumnFormatMixin:
    formats = []
    def row(self, rowdata):
        rowdata = [ (fmt % item) for fmt, item in zip(self.formats, rowdata)]
        super().row(rowdata)

class UpperHeadersMixin:
    def headings(self, headers):
        super().headings([h.upper() for h in headers])

def create_formatter(name, column_formats=None, upper_headers=False):
    if name == 'text':
        formatter_cls = TextTableFormatter
    elif name == 'csv':
        formatter_cls = CSVTableFormatter
    elif name == 'html':
        formatter_cls = HTMLTableFormatter
    else:
        raise RuntimeError('Unknown format %s' % name)

    if column_formats:
        class formatter_cls(ColumnFormatMixin, formatter_cls):
              formats = column_formats

    if upper_headers:
        class formatter_cls(UpperHeadersMixin, formatter_cls):
            pass

    return formatter_cls()
```

最后，还需要如下 `tableformat/__init__.py`：

```python
# tableformat/__init__.py

from .formatter import print_table, create_formatter

__all__ = [ 'print_table', 'create_formatter' ]
```


[返回](ex9_3.md)
