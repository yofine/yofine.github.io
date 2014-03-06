
##javascript


----------


>继承


----------


###原型链

>实现

```js
function SuperType () {
  this.property = true;
}

SuperType.prototype.getSuperValue = function() {
  return this.property;
};

function SubType () {
  this.subproperty = false;
}

SubType.prototype = new SuperType();

SubType.prototype.getSubValue = function() {
  return this.subproperty;
};

var instance = new SubType();

console.log(instance.getSuperValue());

console.log(instance instanceof Object);  //true
console.log(instance instanceof SuperType);  //true
console.log(instance instanceof SubType);  //true

console.log(Object.prototype.isPrototypeOf(instance));  //true
console.log(SuperType.prototype.isPrototypeOf(instance));  //true
console.log(SubType.prototype.isPrototypeOf(instance));  //true
```
>原型链的问题

- 在通过原型链来实现继承时， 原型实际会变成另一个类型的实例(篡改原型)。
- 在创建子类型的实例时， 不能向超类型的构造函数中传递参数。


----------

###借用构造函数

>实现

```js
function SuperType () {
  this.color = ['red', 'blue', 'green'];
}

function SubType () {
  SuperType.call(this);
}

var instance1 = new SubType();
instance1.color.push('black');
console.log(instance1.color);  // 'red, blue, green, black'

var instance2 = new SubType();
console.log(instance2.color);  // 'red, blue, green'
```
>传递参数

```js
function SuperType (name) {
  this.name = name;
}

function SubType () {
  SuperType.call(this, 'yofine');
  this.age = 25;
}

var instance = new SubType();
console.log(instance.name);  // 'yofine'
console.log(instance.age);  //25
```
>借用构造函数的问题

- 无法复用
- 在超类型的原型中定义的方法， 对子类型而言是不可见的


----------

###组合继承

>实现

```js
function SuperType (name) {
  this.name = name;
  this.colors = ['red', 'blue', 'green'];
}

SuperType.prototype.sayName = function() {
  console.log(this.name);
};

function SubType (name. age) {
  SuperType.call(this, name);
  this.age = age;
}

SubType.prototype = new SuperType();
SubType.prototype.constructor = SubType;
SubType.prototype.sayAge = function() {
  console.log(this.age);
}

var instance1 = new SubType('yofine', 25);
instance1.colors.push('black');
console.log(instance1.colors);  //'red, blue, green, black'
instance1.sayName();  //yofine
instance1.sayAge();  //25

var instance2 = new SubType('dante', 25);
console.log(instance2.colors);  //'red, blue, green'
instance2.sayName();  //dante
instance2.sayAge();  //25
```

>组合继承避免了原型链和借用构造函数的缺陷， 融合了它们的优点， 成为JavaScript中最常用的继承模式


----------

###原型式继承

>实现

```js
function object(o) {
  function F() {}
  F.prototype = o;
  return new F();
}


if (typeof Object.create !== 'function') {
  Object.create = function(o) {
    function F() {}
    F.prototype = o;
    return new F();
  };
}
```


----------


###寄生式继承

>实现

```js
function createAnother(original) {
  var clone = object(original);
  clone.sayHi = function() {
    console.log('hi');
  };
  return clone;
}
```

>问题

- 无法复用


----------

###寄生组合式继承

>实现

```js
function inheritPrototype(subType, superType) {
  var prototype = object(superType.prototype);
  prototype.constructor  = subType;
  subType.prototype = prototype;
}
```


----------


###深拷贝

```js
function deepCopy(p, c) {
  c = c || {};
  for (var i in p) {
    if (typeof p[i] === 'object') {
      c[i] = (p[i].constructor === Array) ? [] : {};
      arguments.callee(p[i], c[i]);
    } else {
      c[i] = p[i];
    }
  }
  return c;
}

```

###浅拷贝

```js
function extendCopy(p) {
  var c = {};
  for (var i in p) {
    c[i] = p[i];
  }
  return c;
}
```
>问题  篡改原型


----------

###绑定

```js
Function.prototype.bind = Function.prototype.bind || function(context){
  var self = this;

  return function(){
    return self.apply(context, arguments);
  };
}
```


----------
###缓存

```js
function memorize(f) {
  var cache = {};
  return function() {
    var key = arguments.length + Array.prototype.join.call(arguments, ',');
    if (key in cache) return cache[key];
    return cache[key] = f.apply(this, arguments);
  }
}

```


----------
###不完全函数

```js
function array(a, n) {
  return Array.prototype.slice.call(a, n || 0);
}

function partial(f) {
  var args = arguments;
  return function() {
    var a = array(args, 1);
    var i = 0;
    var j = 0;
    for (; i < a.length; i++) {
      if(a[i] === undefined) a[i] = arguments[j++];
    }
    a = a.concat(array(arguments, j));
    return f.apply(this, a);
  }
}
```


----------
###静态文件服务器

```js
var PORT = process.argv[2] || 8000;
var http = require("http");
var url = require("url");
var fs = require("fs");
var path = require("path");
var mime = require("./mime").types;
var config = require("./config");
var utils = require("./utils");
var zlib = require("zlib");

var server = http.createServer(function(request, response) {
    response.setHeader("Server", "Node/V5");
    response.setHeader('Accept-Ranges', 'bytes');
    var pathname = url.parse(request.url).pathname;
    if (pathname.slice(-1) === "/") {
        pathname = pathname + config.Welcome.file;
    }
    var realPath = path.join("assets", path.normalize(pathname.replace(/\.\./g, "")));

    var pathHandle = function (realPath) {
        fs.stat(realPath, function (err, stats) {
            if (err) {
                response.writeHead(404, "Not Found", {'Content-Type': 'text/plain'});
                response.write("This request URL " + pathname + " was not found on this server.");
                response.end();
            } else {
                if (stats.isDirectory()) {
                    realPath = path.join(realPath, "/", config.Welcome.file);
                    pathHandle(realPath);
                } else {
                    var ext = path.extname(realPath);
                    ext = ext ? ext.slice(1) : 'unknown';
                    var contentType = mime[ext] || "text/plain";
                    response.setHeader("Content-Type", contentType);
                    response.setHeader('Content-Length', stats.size);

                    var lastModified = stats.mtime.toUTCString();
                    var ifModifiedSince = "If-Modified-Since".toLowerCase();
                    response.setHeader("Last-Modified", lastModified);

                    if (ext.match(config.Expires.fileMatch)) {
                        var expires = new Date();
                        expires.setTime(expires.getTime() + config.Expires.maxAge * 1000);
                        response.setHeader("Expires", expires.toUTCString());
                        response.setHeader("Cache-Control", "max-age=" + config.Expires.maxAge);
                    }

                    if (request.headers[ifModifiedSince] && lastModified == request.headers[ifModifiedSince]) {
                        response.writeHead(304, "Not Modified");
                        response.end();
                    } else {
                        var compressHandle = function (raw, statusCode, reasonPhrase) {
                                var stream = raw;
                                var acceptEncoding = request.headers['accept-encoding'] || "";
                                var matched = ext.match(config.Compress.match);

                                if (matched && acceptEncoding.match(/\bgzip\b/)) {
                                    response.setHeader("Content-Encoding", "gzip");
                                    stream = raw.pipe(zlib.createGzip());
                                } else if (matched && acceptEncoding.match(/\bdeflate\b/)) {
                                    response.setHeader("Content-Encoding", "deflate");
                                    stream = raw.pipe(zlib.createDeflate());
                                }
                                response.writeHead(statusCode, reasonPhrase);
                                stream.pipe(response);
                            };

                        if (request.headers["range"]) {
                            var range = utils.parseRange(request.headers["range"], stats.size);
                            if (range) {
                                response.setHeader("Content-Range", "bytes " + range.start + "-" + range.end + "/" + stats.size);
                                response.setHeader("Content-Length", (range.end - range.start + 1));
                                var raw = fs.createReadStream(realPath, {"start": range.start, "end": range.end});
                                compressHandle(raw, 206, "Partial Content");
                            } else {
                                response.removeHeader("Content-Length");
                                response.writeHead(416, "Request Range Not Satisfiable");
                                response.end();
                            }
                        } else {
                            var raw = fs.createReadStream(realPath);
                            compressHandle(raw, 200, "Ok");
                        }
                    }
                }
            }
        });
    };

    pathHandle(realPath);
});

server.listen(PORT);
console.log("Server running at port: " + PORT + ".");
```