# about-tornado

Tornado is a Python web framework and asynchronous networking library, originally developed at FriendFeed. By using non-blocking network I/O, Tornado can scale to tens of thousands of open connections, making it ideal for long polling, WebSockets, and other applications that require a long-lived connection to each user.

译：Tornado是一个轻量级的python框架，可编写强大的，可扩展的Web服务器，也能被用在大量的应用和工具中。
## Install Tornado

#### pip安装
```
    $ pip install tornado
```
#### Github源码编译安装
```
    $ curl -L -O https://github.com/facebook/tornado/archive/v3.1.0.tar.gz
    $ tar xvzf v3.1.0.tar.gz
    $ cd tornado-3.1.0
    $ python setup.py build
    $ sudo python setup.py install
```

## Hello Tornado

#### 创建你的第一个Tornado应用，hello.py:

```python
    import tornado.httpserver
    import tornado.ioloop
    import tornado.options
    import tornado.web

    from tornado.options import define, options
    define("port", default=8000, help="run on the given port", type=int)

    class IndexHandler(tornado.web.RequestHandler):
        def get(self):
            self.write('Hello Tornado!')

    if __name__ == "__main__":
        tornado.options.parse_command_line()
        app = tornado.web.Application(handlers=[(r"/", IndexHandler)])
        http_server = tornado.httpserver.HTTPServer(app)
        http_server.listen(options.port)
        tornado.ioloop.IOLoop.instance().start()
```

#### 命令行运行程序:

```
    $ python hello.py --port=8000
```

#### 在浏览器中打开http://localhost:8000，或者打开另一个终端窗口使用curl测试我们的应用：

```
    $ curl http://localhost:8000/
```

## License

[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2016 xiaoming
