## On Ubuntu 22 ARM[^1]

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source .bashrc
nvm install --lts
nvm use --lts
npm install -g pm2
pm2 dump
pm2 startup
# pm2 unstartup
```

```sh
# Restore from dump file after reboot
pm2 resurrect
```

## Config

### On Windows 10

```sh
set "PM2_HOME=C:\ProgramData\pm2\home"
set "PM2_INSTALL_DIRECTORY=C:\ProgramData\npm\npm\node_modules\pm2"
set "PM2_SERVICE_DIRECTORY=C:\ProgramData\pm2\service"
```

### Configuare Apache on Rocky Linux[^2][^3]

```sh
pm2 start npm --name "<app_name>" --watch -- start
```

Create a new VirtualHost configuration with subdomain names:

```sh
sudo vim /etc/httpd/conf.d/sub.domain.com.conf
```

```
<VirtualHost *:80>
  ServerName www.sub.domain.com
  ServerAlias sub.domain.com

  ErrorLog /var/log/httpd/sub.domain.com-error.log
  CustomLog /var/log/httpd/sub.domain.com-access.log combined
  ProxyPreserveHost On
  ProxyPass / http://localhost:3000/
  ProxyPassReverse / http://localhost:3000/
</VirtualHost>
```

[^1]: [Persistent applications](https://pm2.keymetrics.io/docs/usage/startup/)
[^2]: [How to specify a port number for pm2](https://stackoverflow.com/questions/31502351/how-to-specify-a-port-number-for-pm2)
[^3]: [How to change the port in nextjs?](https://medium.com/frontendweb/how-to-change-port-in-nextjs-1b99930bb81f)