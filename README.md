[Travis Widget]: https://img.shields.io/travis/kataras/go-serializer.svg?style=flat-square
[Travis]: http://travis-ci.org/kataras/go-serializer
[License Widget]: https://img.shields.io/badge/license-MIT%20%20License%20-E91E63.svg?style=flat-square
[License]: https://github.com/kataras/go-serializer/blob/master/LICENSE
[Release Widget]: https://img.shields.io/badge/release-v0.0.3-blue.svg?style=flat-square
[Release]: https://github.com/kataras/go-serializer/releases
[Chat Widget]: https://img.shields.io/badge/community-chat-00BCD4.svg?style=flat-square
[Chat]: https://kataras.rocket.chat/channel/go-serializer
[ChatMain]: https://kataras.rocket.chat/channel/go-serializer
[ChatAlternative]: https://gitter.im/kataras/go-serializer
[Report Widget]: https://img.shields.io/badge/report%20card-A%2B-F44336.svg?style=flat-square
[Report]: http://goreportcard.com/report/kataras/go-serializer
[Documentation Widget]: https://img.shields.io/badge/documentation-reference-5272B4.svg?style=flat-square
[Documentation]: https://godoc.org/github.com/kataras/go-serializer
[Language Widget]: https://img.shields.io/badge/powered_by-Go-3362c2.svg?style=flat-square
[Language]: http://golang.org
[Platform Widget]: https://img.shields.io/badge/platform-any--OS-yellow.svg?style=flat-square



Serialize any custom type to []byte or string.
Your custom serializers are finally, organised.

[![Travis Widget]][Travis] [![Release Widget]][Release] [![Documentation Widget]][Documentation] [![Chat Widget]][Chat] [![Report Widget]][Report] [![License Widget]][License]  [![Language Widget]][Language] ![Platform Widget]

**Easy-to-use** while providing robust set of features, simple to understand.

Built'n supported serializers:

- [JSON](https://github.com/kataras/go-serializer/tree/master/json)
- [JSONP](https://github.com/kataras/go-serializer/tree/master/jsonp)
- [XML](https://github.com/kataras/go-serializer/tree/master/xml)
- [Markdown](https://github.com/kataras/go-serializer/tree/master/markdown)
- [Text](https://github.com/kataras/go-serializer/tree/master/text)
- [Binary Data](https://github.com/kataras/go-serializer/tree/master/data)

Go [here](https://github.com/kataras/go-serializer/blob/master/serializer.go#L12) to learn how you can create and use your own custom Serializer.


This package is already used by [Iris web framework](https://github.com/kataras/iris) and [Q web framework](https://github.com/kataras/q).


Installation
------------
The only requirement is the [Go Programming Language](https://golang.org/dl), at least v1.6.

```bash
$ go get -u github.com/kataras/go-serializer
```


Usage
------------

```go
package main

import (
  "github.com/kataras/go-serializer"
  "github.com/kataras/go-serializer/markdown"
)

func main() {
  markdownSerializer := markdown.New()

  serializer.For("markdown", markdownSerializer)

  result, err := serializer.SerializeToString("markdown", "## Hello")
  // Optional third parameter is a map[string]interface{}, which is any runtime options for the serializers registered to 'markdown' key

  println(result)
}
```

**explanation**

Create your own serializer or use one of the project's built'n serializers, in this case we will use the markdown serializer
will receive markdown content as string and return the HTML form of them
```go
markdownSerializer := markdown.New()
```
> Learn how to create your own custom serializer go to the serializer_test.go, it's just one function.

```go
mySerializers := serializer.Serializers{}
mySerializers.For("key", markdownSerializer)
```


Add the serializer to a custom key, using the default Serializers{}.
It supports more than one serializer for each key

```go
serializer.For("markdown", markdownSerializer)
```

Serialize something with the registered serializers by a key.
If more than one Serializer is registered to the same key then
the final result will be the results of all of its(key's) serializers
```go
result, err := serializer.SerializeToString("markdown", "## Hello")
```

> .Serialize(...) returns []byte, SerializeToString(...) returns string, they're the same use that you need

Print the result, will be just a `<h2>Hello</h2>`
```go
println(result)
```


For more, please read each of the Serializers you want to use, built'n supported are:

- [JSON](https://github.com/kataras/go-serializer/tree/master/json)
- [JSONP](https://github.com/kataras/go-serializer/tree/master/jsonp)
- [XML](https://github.com/kataras/go-serializer/tree/master/xml)
- [Markdown](https://github.com/kataras/go-serializer/tree/master/markdown)
- [Text](https://github.com/kataras/go-serializer/tree/master/text)  (exists for your learning curve)
- [Binary Data](https://github.com/kataras/go-serializer/tree/master/data)  (exists for your learning curve)


You can also navigate to the [godocs](https://godoc.org/github.com/kataras/go-serializer).

FAQ
------------

If you'd like to discuss this package, or ask questions about it, feel free to

 * Explore [these questions](https://github.com/kataras/go-serializer/issues?go-serializer=label%3Aquestion).
 * Post an issue or  idea [here](https://github.com/kataras/go-serializer/issues).
 * Navigate to the [Chat][Chat].



Versioning
------------

Current: **v0.0.3**

Read more about Semantic Versioning 2.0.0

 - http://semver.org/
 - https://en.wikipedia.org/wiki/Software_versioning
 - https://wiki.debian.org/UpstreamGuide#Releases_and_Versions



People
------------
The author of go-serializer is [@kataras](https://github.com/kataras).


Contributing
------------
If you are interested in contributing to the go-serializer project and add more serializers, please make a PR.

License
------------

This project is licensed under the MIT License.

License can be found [here](LICENSE).
