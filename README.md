# google-cloud-notes

1、**ubuntu** 系统通过 **ufw** 开启端口之后，还要添加 **google cloud** 防火墙规则
 
```
如果你已经在 Ubuntu 的 UFW 中打开了端口 1080，但仍然看到 "filtered" 的状态，这可能是由于 Google Cloud Platform 的防火墙规则尚未正确设置。请确保在 Google Cloud Platform 的 "VPC network" > "Firewall rules" 设置中，你已为端口 1080 创建了适当的入站规则。

如果在 GCP 的防火墙中已经打开了端口，而端口仍显示为 "filtered"，那么可能的原因可能包括：

服务没有运行或没有正确配置：检查运行在 1080 端口的服务是否正在运行并且正确配置。如果是 SOCKS 服务，确认它被配置为在正确的 IP 地址（例如 0.0.0.0 或特定的公网 IP）和端口上监听。
其他网络设备的防火墙或过滤规则：如果你的服务器连接到了其他的网络设备（例如额外的防火墙，路由器或负载均衡器），这些设备可能有自己的防火墙规则，需要单独配置。
一般来说，"filtered" 状态的端口意味着网络访问被阻止。你需要检查所有可能的层面，包括服务器防火墙（如 UFW），云平台的防火墙（如 GCP），服务的配置，以及任何额外的网络设备或服务。
```

验证是否开启成功
```
❯ nmap x.x.x.x -p 1080
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-15 16:35 PST
Nmap scan report for x.x.x.x.bc.googleusercontent.com (x.x.x.x)
Host is up (0.19s latency).

PORT     STATE SERVICE
1080/tcp open  socks

Nmap done: 1 IP address (1 host up) scanned in 0.45 seconds
``
