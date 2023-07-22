"# create a service for dotnet application to be run on systemctl" 

# 1-create file in /etc/systemd/system/app.service

# 2-copy code to the file, don't forget to replcae applicaiton name and path

> [Unit] 
> Description= dotnet core 7 webapp
> [Service] 
WorkingDirectory=/var/www/dotnetwebapp
ExecStart=/usr/bin/dotnet /var/www/dotnetwebapp/WepAppHostOnNginx.dll 
Restart=always
# Restart service after 10 seconds if the dotnet service crashes:
RestartSec=10
SyslogIdentifier=WepAppHostOnNginx
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target

# 3- enable the service by execte following command
> systemctl enable dotnetwebapp.service

# 4- start the service
> sudo systemctl start dotnetwebapp.service

