---
title: modbus串口通信
date: 2023-02-25 15:39:03
tags: 
- python
- serial
categories: note
# 加入时间线
selected: true
---

浅浅记录一下，之前做老化柜电压电流，以及电阻测试仪数据采集用到的串口通信

使用python serial模块进行的串口通信。

<!-- more -->

### serial模块的使用方法
``` python
# 引入serial模块
import serial

# 端口，GNU / Linux上的/ dev / ttyUSB0 等 或 Windows上的 COM3 等
# 波特率，标准值之一：50,75,110,134,150,200,300,600,1200,1800,2400,4800,9600,19200,38400,57600,115200
# 超时设置,None：永远等待操作，0为立即返回请求结果，其他值为等待超时时间(单位为秒）
def openPort(portx, bps, timeout):
  ret = False
  try:
    # 打开串口，并得到串口对象
    ser = serial.Serial(portx, bps, timeout = timeout)
    # 判断串口是否打开
    if(ser.is_open):
      ret = True
  except Exception as e:
    # 如果异常则输出异常原因
    print("---Error---", e)
  return ser, ret
```

### 发送数据
``` python
# 引入serial模块
import serial
if __name__ == '__main__':
  ser = serial.Serial('COM1', 9600, None)
  if(ser.is_open):
    aa = '46 45 54 43 68 3F 0A'  # 这里使用十六进制数，数据的类型根据对应的协议进行更改
    bb = bytes.fromhex(aa)  # 数据转换为bytes类型
    result = ser.write(bb)  # 发送数据
    print result  # 查看发送数据
```

### 接收数据
``` python
# 引入serial模块
import serial
if __name__ == '__main__':
  ser = serial.Serial('COM1', 9600, None)
  if(ser.is_open):
    count = ser.in_waiting  # 返回数据的字节数
    data = ser.read(count)  # 使用read接收数据
    print data  # 输出接收的数据
```

### serial模块常用的方法
| 方法 | 说明 |
| :-- | :-- |
| ser.open() | 打开端口 |
| ser.close() | 关闭端口 |
| ser.is_open | 查看端口是否打开 |
| ser.write() | 发送数据 |
| ser.read() | 接收数据，可指定字节数，默认为1 |
| ser.readline() | 接收一行数据 |
| ser.read_all | 接收全部数据 |
| ser.in_waitting | 返回数据的字节数 |
| ser.flush() | 等待所有数据发出 |
| ser.flushInput | 丢弃接收缓存中的所有数据 |
| ser.flushOutput() | 终止当前发送操作，并丢弃发送缓存中的数据 |