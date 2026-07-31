## Enable POP and IMAP

- IMAP server: imap.domain.com, port 993
- SMTP server: smtp.domain.com, port 465/587

- [Outlook](https://outlook.live.com) → Settings → Mail → Forwarding and IMAP → POP and IMAP
	Outlook → Account → My Microsoft account → Privacy → Apps and services that can access your data
- [Yandex Mail](https://mail.yandex.com) → Settings → All settings → Email clients
- [QQ邮箱](https://wx.mail.qq.com/) → 设置 → 账号 → POP3/IMAP/SMTP/Exchange/CardDAV/CalDAV服务
- [网易邮箱](https://mail.163.com) → 设置 → POP3/SMTP/IMAP

## Message Filters

- Thunderbird → More → Tools → Message Filters
	1. Filters for `your@email.com`
	2. New ...
		1. Filter name: `blacklist`
		2. Match all of the following → Add (all you want to match) → For example, `From` `contains` `example01@spam.com`
		3. Perform these actions → `Set Junk Status to` `Junk` or `Move Message to` `Junk on your@email.com`
		4. OK