# aiblock - nginx

* Copy `aiblock.conf` to `/etc/nginx/snippets`.
* Copy `aiblock-errorpage.conf` to `/etc/nginx/snippets`.
* Copy `402.html` to `/var/www/aiblock`.

Include `aiblock.conf` on the end of each `location` block. Examples:

```
location / {
    include /etc/nginx/snippets/aiblock.conf;

    try_files $uri $uri/ =404;
}

location = /metrics {
    include /etc/nginx/snippets/aiblock.conf;

    proxy_pass http://localhost:9100/metrics;
}
```

Include `aiblock-location.conf` on the end of each `server` block. Example:

```
server {
    # ...

    include /etc/nginx/snippets/aiblock-errorpage.conf;
}
```