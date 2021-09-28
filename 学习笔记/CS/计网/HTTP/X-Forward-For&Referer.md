# X-Forwarded-For&Referer
（1）X-Forwarded-For:简称XFF头，它代表客户端，也就是HTTP的请求端真实的IP，只有在通过了HTTP 代理或者负载均衡服务器时才会添加该项。xff 是http的拓展头部，作用是使Web服务器获取访问用户的IP真实地址（可伪造）。由于很多用户通过代理服务器进行访问，服务器只能获取代理服务器的IP地址，而xff的作用在于记录用户的真实IP，以及代理服务器的IP。格式为：X-Forwarded-For: 本机IP, 代理1IP, 代理2IP, 代理2IP

（2）HTTP Referer是header的一部分，当浏览器向web服务器发送请求的时候，一般会带上Referer，告诉服务器我是从哪个页面链接过来的，服务器基此可以获得一些信息用于处理。referer 是http的拓展头部，作用是记录当前请求页面的来源页面的地址。服务器使用referer确认访问来源，如果referer内容不符合要求，服务器可以拦截或者重定向请求。
