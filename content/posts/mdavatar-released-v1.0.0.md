+++
title = "MDAvatar 头像生成器 v1.0.0 [支持中文]"
description = "MDAvatar 可以根据字符串生成单字符头像，并且可以高度自定义，支持生成中文头像"
tags = [
    "go",
    "golang",
    "github",
    "mdavatar",
    "avatar",
]
date = "2020-12-01"
categories = [
    "mdavatar",
    "golang",
]
menu = "main"
+++

# MDAvatar

![](https://static.gocn.vip/photo/2020/70ad5a74-d9b1-4c1b-b694-57af4889a361.png?x-oss-process=image/resize,w_1920)

**MDAvatar** 可以根据字符串生成单字符头像，并且可以高度自定义，支持生成中文头像

高度自定义

- Require `go` version >= `1.13`
- Require `go mod` enable

```bash
$ go get -u github.com/laojianzi/mdavatar
```

## 大写首字母

```go
package main

import (
	"fmt"
	"image/png"
	"log"
	"os"
	"time"

	"github.com/laojianzi/mdavatar"
)

func main() {
	avatar, err := mdavatar.New("laojianzi").Build()
	if err != nil {
		log.Fatal(err)
	}

	filename := fmt.Sprintf("out-%d.png", time.Now().Unix())
	file, err := os.Create(filename)
	if err != nil {
		log.Fatal(err)
	}

	if err := png.Encode(file, avatar); err != nil {
		log.Fatal(err)
	}
}
```

![](https://static.gocn.vip/photo/2020/e2ecad5f-cf0c-472c-b2bc-32553167afc3.png?x-oss-process=image/resize,w_1920)

## 中文转大写首字母

```go
package main

import (
	"fmt"
	"image/png"
	"log"
	"os"
	"time"

	"github.com/laojianzi/mdavatar"
)

func main() {
	avatar, err := mdavatar.New("老健仔").Build()
	if err != nil {
		log.Fatal(err)
	}

	filename := fmt.Sprintf("out-%d.png", time.Now().Unix())
	file, err := os.Create(filename)
	if err != nil {
		log.Fatal(err)
	}

	if err := png.Encode(file, avatar); err != nil {
		log.Fatal(err)
	}
}
```

![](https://static.gocn.vip/photo/2020/de6c577e-b8a3-47a7-82d9-7589e18f5121.png?x-oss-process=image/resize,w_1920)

# 第一个中文

```go
package main

import (
	"fmt"
	"image/png"
	"log"
	"os"
	"time"

	"github.com/laojianzi/mdavatar"
)

func main() {
	avatar, err := mdavatar.New("老健仔", mdavatar.WithAsianFont("static/NotoSansSC-Regular.otf")).Build()
	if err != nil {
		log.Fatal(err)
	}

	filename := fmt.Sprintf("out-%d.png", time.Now().Unix())
	file, err := os.Create(filename)
	if err != nil {
		log.Fatal(err)
	}

	if err := png.Encode(file, avatar); err != nil {
		log.Fatal(err)
	}
}
```

![](https://static.gocn.vip/photo/2020/3997db6a-5128-492c-ba86-12ffca555eb5.png?x-oss-process=image/resize,w_1920)

## 待补充

- 支持 cli (生成 png/jpg)
- 支持自定义形状 (圆形、椭圆形、方形 ...)
- 支持多种返回形式 (HTTP、Base64、WriteToFile ...)

## 项目地址

欢迎大家使用 [MDAvatar](https://github.com/laojianzi/mdavatar)

如果喜欢帮忙 Srat 和 Fork，如果有疑问可以提 [Issue](https://github.com/laojianzi/mdavatar/issues) 或者 [Email](mailto:laojianzi1994@gmail.com)

**Github**: https://github.com/laojianzi/mdavatar
