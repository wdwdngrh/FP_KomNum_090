```
nano /var/www/html/profile_sciel.html
```

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sciel</title>
<style>
  body {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    color: #fff;
    background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
    background-size: 800% 800%;
    animation: bgShift 20s ease infinite;
  }
  @keyframes bgShift {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
  }
  .container {
    max-width: 700px;
    margin: 4rem auto;
    background: rgba(255, 255, 255, 0.08);
    border-radius: 16px;
    padding: 2.5rem;
    box-shadow: 0 4px 20px rgba(0,0,0,0.5);
    backdrop-filter: blur(6px);
  }
  h1 {
    text-align: center;
    color: #00e5ff;
    text-shadow: 0 0 10px #00e5ff;
  }
  h2 {
    color: #ffd166;
    margin-top: 1.5rem;
  }
  p, li { line-height: 1.6; }
  ul { list-style: none; padding-left: 0; }
  li::before { content: "▹ "; color: #00e5ff; }
  footer { text-align: center; font-size: 0.85rem; color: #ccc; margin-top: 2rem; }
</style>
</head>
<body>
  <div class="container">
    <h1>Sciel</h1>
    <p><i>“Tomorrow comes.”</i></p>

    <h2>Core Expertise</h2>
    <ul>
      <li>Stealth and Infiltration Tactics</li>
      <li>Long-Range Surveillance</li>
      <li>Navigation and Terrain Mapping</li>
      <li>Rapid Response & Target Acquisition</li>
    </ul>

    <h2>Profile Summary</h2>
    <p>Sciel serves as the eyes and ears of Expedition 33. 
       Agile and perceptive, he scouts ahead, tracks enemy movement, 
       and secures safe passage before every major confrontation.</p>
  </div>

  <footer>© 2025 Expedition 33 — For Those Who Come After</footer>
</body>
</html>
```

```
nano /etc/nginx/sites-available/jarkom
```

```
server {
    listen 80;
    server_name sciel33.com;

    root /var/www/html;
    index profile_sciel.html;

    log_format custom_log '[$time_local] Jarkom Node Sciel Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
                               
    access_log /tmp/access.log custom_log;
    error_log  /tmp/error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

```
ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled/jarkom
```

```
service nginx restart
```

```
nginx -t
```
