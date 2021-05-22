# 使用 curl 发送 POST 请求的几种方式

HTTP 的 POST 请求通常是用于提交数据，可以通过这篇文章来了解各种提交方式：[四种常见的 POST 提交数据方式](https://imququ.com/post/four-ways-to-post-data-in-http.html)。做 Web 后端开发时，不可避免地要自己给自己发请求来调试接口，这里要记录的内容是如何使用命令行工具 `curl` 来进行各种方式的 POST 请求。

## `application/x-www-form-urlencoded`

最常见的一种 POST 请求，用 curl 发起这种请求也很简单。

```shell-session
$ curl localhost:3000/api/basic -X POST -d 'hello=world'
```

## `multipart/form-data`

这种请求一般涉及到文件上传。后端对这种类型请求的处理也复杂一些。

```shell-session
$ curl localhost:3000/api/multipart -F raw=@raw.data -F hello=world
```

## `application/json`

```shell-session
$ curl localhost:3000/api/json -X POST -d '{"hello": "world"}' --header "Content-Type: application/json"
```

跟发起 `application/x-www-form-urlencoded` 类型的 POST 请求类似，`-d` 参数值是 JSON 字符串，并且多了一个 `Content-Type: application/json` 指定发送内容的格式。

这个例子和 `application/x-www-form-urlencoded` 中的例子发起的请求，到了 Web 后端经过解析后，得到的结果都是 `hello: world` 键值对。

## 把文件内容作为要提交的数据

如果要提交的数据不像前面例子中只有一个 `hello: world` 键值对，数据比较多，都写在命令行里很不方便，也容易出错，那么可以把数据内容先写到文件里，通过 `-d @filename` 的方式来提交数据。这是 `-d` 参数的一种使用方式，所以前面用到 `-d` 参数的地方都可以这样用。

**实际上就是把 `-d` 参数值写在命令行里，变成了写在文件里**。跟 `multipart/form-data` 中上传文件的 POST 方式**不是**一回事。`@` 符号表明后面跟的是文件名，要读取这个文件的内容作为 `-d` 的参数。

例如，有一个 JSON 文件 `data.json` 内容如下:

```json
{
    "hello": "world",
    "xxx": "yyy",
    "a": ["ooo", "mmm"]
}
```

就可以通过

```shell-session
$ curl localhost:3000/api/json -X POST -d @data.json --header "Content-Type: application/json"
```

来提交数据。

如果要用 `application/x-www-form-urlencoded` 方式提交，后端解析出来同样的数据，那么 `-d` 的参数是这样的（注意数组参数的写法）

```
hello=world&xxx=yyy&a[]=ooo&a[]=mmm
```

把这个字符串直接作为 `-d` 的参数或者把它写到文件 `data.txt` 然后通过 `-d @data.txt` 的方式，发起 POST 请求，行为和结果是一样的。

```shell-session
$ curl localhost:3000/api/basic -X POST -d 'hello=world&xxx=yyy&a[]=ooo&a[]=mmm'

$ curl localhost:3000/api/basic -X POST -d @data.txt
```