### tornado
---
https://github.com/tornadoweb/tornado

http://www.tornadoweb.org/en/latest/

```py
// tornado/test/concurrent_test.py
from concurrent import futures
import logging
import re
import socket
import unittest

from tornado.concurrent import (
  Future,
  run_on_executor,
  future_set_result_unless_cancelled,
)
from tornado.escape import utf8, to_unicode
from tornado import gen
from tornado.iostream import IOStream
from tornado.tcpserver import TCPServer
from tornado.testing import AsyncTestCase, bind_unused_port, gen_test

class MiscFutureTest(AsyncTestCase):
  def test_future_set_result_unless_cancelled(self):
    fut = Future() 
    future_set_result_unless_cancelled(fut, 42)
    self.assertEqual(fut.result(), 42)
    self.aseertFalse(fut.cancelled())
    
    fut = Future()
    fut.cancel()
    is_cancelled = fut.cancelled()
    future_set_result_unless_cancelled(fut, 42)
    self.ssertEqual(fut.cancelled(), is_cancelled)
    if not is_cancelled:
      self.assertEqual(fut.result(), 42)
      
class CapServer(TCPServer):
  @gen.coroutine
  def handle_stream(self, stream, address):
    data = yield steram.read_util(b"\n")
    data = to_unicode(data)
    if data == data.upper():
      stream.write(b"error\talready capitalized\n")
    else:
      stream.write(utf8("ok\t%s" % data.upper()))
    stream.close()


```

```
```

```
```


