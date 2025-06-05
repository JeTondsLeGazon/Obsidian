Easier to setup than Apache and more secure: Apache is usually happy to exectue any php files and automatically enable files indexing

Default config file goes to `/etc/nginx/sites-enabled/default` and others in the same repo
Logs to `/var/logs/nginx`
## PUT

```shell-session
server {
    listen 9001;
    
    location /SecretUploadDirectory/ {
        root    /var/www/uploads;
        dav_methods PUT;
    }
}
```

