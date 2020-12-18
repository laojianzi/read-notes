+++
title = "MDAvatar v1.0.1 圆形支持 - 说肝就肝"
description = "MDAvatar 可以根据字符串生成单字符头像，并且可以高度自定义，支持生成中文头像"
tags = [
    "go",
    "golang",
    "github",
    "mdavatar",
    "avatar",
]
date = "2020-12-02"
categories = [
    "mdavatar",
    "golang",
]
menu = "main"
+++

刚发布 v1.0.0 [MDAvatar 头像生成器 v1.0.0 \[支持中文\]](/read-notes/posts/mdavatar-released-v1.0.0) 不久，觉得圆形还是比较刚需，其实也可以 `方形图 + css` 实现 web 的圆形 img

不过......

> 支持总好过不支持

---

## Release v1.0.1

https://github.com/laojianzi/mdavatar/releases/tag/v1.0.1

### Added

- 支持多种 `style` 构建头像
- 添加圆形头像构建的 `style`

``` go
package main

import (
	"fmt"
	"image/png"
	"log"
	"os"
	"time"

	"github.com/laojianzi/mdavatar"
	"github.com/laojianzi/mdavatar/style"
)

func main() {
	avatar, err := mdavatar.New("MDAvatar").Builds(style.NewCircle)
	if err != nil {
		log.Fatal(err)
	}

	filename := fmt.Sprintf("mdavatar-circle-%d.png", time.Now().Unix())
	file, err := os.Create(filename)
	if err != nil {
		log.Fatal(err)
	}

	if err := png.Encode(file, avatar); err != nil {
		log.Fatal(err)
	}
}
```

![](https://static.gocn.vip/photo/2020/7915dcf2-ea9c-4d24-a440-91b87e28917c.png?x-oss-process=image/resize,w_1920)

## 参考

- https://blog.golang.org/image-draw

## 项目

欢迎大家使用 [MDAvatar](https://github.com/laojianzi/mdavatar)

如果喜欢帮忙 Srat 和 Fork，如果有疑问可以提 [Issue](https://github.com/laojianzi/mdavatar/issues) 或者 [Email](mailto:laojianzi1994@gmail.com)

- Require `go` version >= `1.13`
- Require `go mod` enable

```bash
$ go get -u github.com/laojianzi/mdavatar
```

**Github**: https://github.com/laojianzi/mdavatar

感谢你阅读本文
