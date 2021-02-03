# shadowsocks-libev

## 介绍
基于 [shadowsocks/shadowsocks-libev](https://hub.docker.com/r/shadowsocks/shadowsocks-libev) 集成了 [v2ray-plugin](https://github.com/shadowsocks/v2ray-plugin) 插件。

## 使用

增加 `PLUGIN` 和 `PLUGIN-OPTS` 环境变量，用于指定插件相关信息。（提供值为 `PLUGIN=v2ray-plugin`, `PLUGIN-OPTS=service`）详细配置请参考 [v2ray-plugin#usage](https://github.com/shadowsocks/v2ray-plugin#usage)

### 基于 HTTP
可以在原来使用基础上，不增加任何参数，使用 Shadowsocks over HTTP 方式启动 ss-server 服务。

```shell
docker run --name ss-v2ray -d -e PASSWORD='your password' --restart always -p 5100:8388 eirture/shadowsocks-libev
```

另外需要在客户端中指定 `v2ray-plugin` 插件。macOS ShadowsocksX-NG 为例，在服务器配置中的“插件”栏，填入"v2ray-plugin"。

### 基于 HTTPS

开启 `tls` 功能需要一个域名，并将其绑定运行服务的主机IP。假设您已经有证书和私钥（如果没有请[参考这里](https://github.com/shadowsocks/v2ray-plugin#issue-a-cert-for-tls-and-quic)），将证书和私钥挂载到容器内。v2ray-plugin 默认读取证书和私钥的路径分别为 `~/.acme.sh/{host}/fullchain.cer`， `~/.acme.sh/{host}/{host}.key`。此路径可以在 `PLUGIN-OPTS` 中指定。开启 `tls` 还需在插件参数中指定主机域名地址。完整命令如下。

```shell
docker run --name ss-v2rays -d -e PASSWORD='password' -e PLUGIN-OPTS='server;tls;host=ss.eirture.cn' --reastart always -v /root/.acme.sh:/root/.acme.sh -p 5101:8388 eirture/shadowsocks-libev
```

如果证书和私钥在其他位置，将其指定挂载到容器内。然后在 `PLUGIN-OPTS` 指定，如：`PLUGIN-OPTS="xxx;cert=/fullchain.cer;key=/ss.eirture.cn.key"`。

客户端中需要指定“插件”值为 `v2ray-plugin`，及“插件选项”值为 `tls;host=ss.eirture.cn`
