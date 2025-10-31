```
server {
    listen 80;
    server_name expeditioners.com;

    access_log /tmp/expeditioners_access.log;
    error_log /tmp/expeditioners_error.log;

    location /profil_lune {
        proxy_pass http://10.24.2.1:80;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    location /profil_sciel {
        proxy_pass http://10.24.2.2:80;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    location /profil_gustave {
        proxy_pass http://10.24.2.3:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    location / {
        proxy_pass http://10.24.2.1:8000; 
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
