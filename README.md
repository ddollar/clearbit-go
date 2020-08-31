我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

# Clearbit Go Bindings
[![Build Status](https://travis-ci.org/clearbit/clearbit-go.svg?branch=master)](https://travis-ci.org/clearbit/clearbit-go) [![GoDoc](https://godoc.org/github.com/clearbit/clearbit-go?status.svg)](https://godoc.org/github.com/clearbit/clearbit-go/clearbit)

Package clearbit provides a client for using the Clearbit API.

## Usage

To use one of the Clearbit APIs you'll first need to create a client by calling the `NewClient` function.
By default `NewClient` will use a new `http.Client` and will fetch the Clearbit API key from the `CLEARBIT_KEY` environment variable.

The Clearbit API key can be changed with:

```go
  client := clearbit.NewClient(clearbit.WithAPIKey("sk_1234567890123123"))
```

You can tap another `http.Client` with:

```go
  client := clearbit.NewClient(clearbit.WithHTTPClient(&http.Client{}))
```

If you use the httpClient just to set the timeout you can instead use WithTimeout:

```go
  client := clearbit.NewClient(clearbit.WithTimeout(20 * time.Second))
```

All options can be combined and the order is not important.

Once the client is created you can use any of the Clearbit APIs

```go
	client.Autocomplete
	client.Company     
	client.Discovery   
	client.Person      
	client.Prospector  
	client.Reveal      
```

Example:

```go
  package main

  import (
      "fmt"
      "github.com/clearbit/clearbit-go/clearbit"
  )

  func main() {
      client := clearbit.NewClient(clearbit.WithAPIKey("sk_1234567890123123"))

      results, resp, err := client.Reveal.Find(clearbit.RevealFindParams{
            IP: "104.193.168.24",
      })

      if err != nil {
        fmt.Println(results, resp)
      }
  }
```

Please see [the examples](https://godoc.org/github.com/clearbit/clearbit-go/clearbit#pkg-examples) for more details.

## License

clearbit-go is copyright © 2016 Clearbit. It is free software, and may
be redistributed under the terms specified in the [`LICENSE`] file.

[`LICENSE`]: /LICENSE
