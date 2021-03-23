# Python3 SMTP发送邮件

SMTP(Simple Mail Transfer Protocol) 即简单邮件传输协议，它是一组用于由
源地址到目的地地址传送邮件的规则，由它来控制信件的中转方式。
python的smtplib提供了一种很方便的途径发送电子邮件。它对smtp协议进行了简单的封装。
Python创建SMTP对象语法如下：

```python
import smtplib

# smtpObj = smtplib.SMTP([host [, port [, local_hostname]]])
```

参数说明：
- host:SMTP服务器主机。你可以指定主机的ip地址或者域名如：runoob.com,这个是可选参数。（纯手敲，非复制- -。）
- port:如果你提供了host参数，你需要指定SMTP服务使用的端口号，一般情况下SMTP端口号为25。
- local_hostname:如果SMTP在你的本机上，你只需要指定服务器地址为localhost即可。

Python SMTP对象使用sendmail方法发送邮件，语法如下

```python
# SMTP.sendmail(from_addr, to_addrs, msg[, mail_options, rcpt_options]
```

参数说明:
- from_addr:邮件发送者地址
- to_addrs:字符串列表，邮件发送地址。
- msg:发送消息
这里要注意一下第三个参数，msg是字符串，表示邮件。