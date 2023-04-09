# ASMR-Downloader

Automatically download doujin voice from [asmr.one](https://www.asmr.one/) .


Linux可执行文件编译
```
go env -w GOOS=linux
go env -w GOARCH=amd64
go build main.go
```
代理设置
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


