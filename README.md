# 扫码盒子客户端

## websocket服务
- 端口 `5678`
- `ws://127.0.0.1:5678`连接
- 发送数据格式为JSON格式

### 连上ws服务收到串口列表
```
{
  "action":"serial_list",
  "data":["COM5","COM6"]
}
```

### 扫码后ws通知消息
```
{
  "action":"scan_qrcode",
  "port":"COM6",
  "data":"扫码内容"
}
```

### 语音播报消息
```
{
  "action":"sound",
  "port":"COM6",
  "data":"Test Voice = 00 sig."
}
```

### 打包脚本
```
pyinstaller -F --clean .\qrbox.py --add-data="demo.html;."
```

### 启动服务
```
qrbox.exe [串口匹配字符串]
```
- 增加传入串口匹配字符串,默认['USB','PCI']
```
qrbox.exe aaa bbb ccc
```
> 这时会匹配连接的串口名称是否包含aaa或bbb或ccc,然后监听对应的串口
