# ASMR-Downloader

音声下载器(https://www.asmr.one/)


1、Linux可执行文件编译
```
go env -w GOOS=linux
go env -w GOARCH=amd64
go build main.go
```
之后会在项目文件夹下输出一个无后缀main文件，linux下用./命令执行,然后输入RJ号即可

2、代理设置
注意：请先确保主机能ping通下载服务器地址（raw.kiko-play-niptan.one）

修改api/client.go代码第51行替换为
```	//HTTP代理
	proxy := "http://192.168.31.3:7890/"
	proxyAddress, _ := url.Parse(proxy)
	client := &http.Client{
		Transport: &http.Transport{
			Proxy: http.ProxyURL(proxyAddress),
		},
	}
	resp, err := client.Do(req)
	//resp, err := c.sendRequest(req)
```  
这里的("http://192.168.31.3:7890/")请替换为自己的代理服务器地址

