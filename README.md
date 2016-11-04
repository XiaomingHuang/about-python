# about-tornado

Tornado is a Python web framework and asynchronous networking library, originally developed at FriendFeed. By using non-blocking network I/O, Tornado can scale to tens of thousands of open connections, making it ideal for long polling, WebSockets, and other applications that require a long-lived connection to each user.

译：Tornado是一个轻量级的python框架，可编写强大的，可扩展的Web服务器，也能被用在大量的应用和工具中。

Documentation and links to additional resources are available at
http://www.tornadoweb.org

## Hello, world

Here is a simple "Hello, world" example web app for Tornado:

    import tornado.ioloop
    import tornado.web

    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            self.write("Hello, world")

    def make_app():
        return tornado.web.Application([
            (r"/", MainHandler),
        ])

    if __name__ == "__main__":
        app = make_app()
        app.listen(8888)
        tornado.ioloop.IOLoop.current().start()

This example does not use any of Tornado's asynchronous features; for
that see this 





