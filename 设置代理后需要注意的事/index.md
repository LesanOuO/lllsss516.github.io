# 设置代理后需要注意的事


如电脑设置了网络代理，会导致一些软件工具不能正常工作。查找了网上许多解决方案，总结如下。

## Git

- 设置全局Config代理

```bash
git config --global http.proxy http://server:port
git config --global https.proxy http://server:port

git config --global http.https://github.com.proxy http://server:port
git config --global https.https://github.com.proxy http://server:port
```

- 去除代理设置

```bash
git config --global --unset http.proxy
git config --global --unset https.proxy

git config --global --unset http.https://github.com.proxy
git config --global --unset https.https://github.com.proxy
```

> 当我使用这种方式时没有效果

- 使用clone时配置代理

```bash
git clone -c http.proxy="server:port" https://github.com/LesanOuO/lesan-homepage.git
```

## NPM

- 全局设置代理

`npm config set proxy http://server:port`

- 配置https代理（设置了proxy就不需要设置https-proxy）

`npm config set https-proxy http://server:port`

- 如果需要代理用户名和密码

```bash
npm config set proxy http://username:password@server:port
npm confit set https-proxy http://username:password@server:port
```

- 取消代理

```bash
npm config delete proxy
npm config delete https-proxy

npm config set proxy null
npm config set https-proxy null
```

## Maven

需要在`settings.xml`中配置`proxies`节点

```xml
...
<proxies>
    <proxy>
        <id>optional</id>
        <active>true</active>
        <protocol>http</protocol>
        <host>127.0.0.1</host>
        <port>8888</port>
    </proxy>
</proxies>
...
```
