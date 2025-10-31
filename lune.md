```
nano /var/www/html/profile_lune.html
```

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lune</title>
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
    <h1>Lune</h1>
    <p><i>“When one falls, we continue.”</i></p>

    <h2>Core Expertise</h2>
    <ul>
      <li>Analysis of Ancient Technologies</li>
      <li>Equipment Calibration & Field Maintenance</li>
      <li>Defense System Deployment</li>
      <li>Data Collection & Anomaly Detection</li>
    </ul>

    <h2>Profile Summary</h2>
    <p>Lune is the mind behind the expedition’s technology. 
       Her understanding of ancient mechanisms and magical artifacts 
       is key to decoding the Paintress’ secrets and keeping the team operational.</p>
  </div>

  <footer>© 2025 Expedition 33 — For Those Who Come After</footer>
</body>
</html>
```

```
nano /etc/nginx/nginx.conf
```

```
log_format custom_log '[$time_local] Jarkom Node Lune Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
```

```
nano /etc/nginx/sites-available/jarkom
```

```
server {
    listen 80;
    server_name lune33.com;

    root /var/www/html;
    index profil_lune.html;
                               
    access_log /tmp/access.log custom_log;
    error_log  /tmp/error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

```
server {
    listen 8000;
    server_name lune33.com;

    root /var/www/html;
    index info.html;

    access_log /tmp/access_info.log;
    error_log /tmp/error_info.log;

    location / {
        try_files $uri $uri/ =404;
    }
}

```

```
nano /var/www/html/info.html
```

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Expedition 33 — Mission Brief</title>
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
  header {
    text-align: center;
    padding: 3rem 1rem 1rem;
  }
  header h1 {
    font-size: 2.8rem;
    color: #00e5ff;
    letter-spacing: 1px;
    text-shadow: 0 0 10px #00e5ff;
  }
  header p {
    font-size: 1rem;
    color: #b5eaff;
    margin-top: 0.3rem;
  }
  .container {
    max-width: 700px;
    margin: 2rem auto 3rem;
    background: rgba(255, 255, 255, 0.08);
    border-radius: 16px;
    padding: 2rem 2.5rem;
    box-shadow: 0 4px 20px rgba(0,0,0,0.4);
    backdrop-filter: blur(6px);
  }
  h2 {
    color: #00e5ff;
    margin-top: 1.5rem;
  }
  p, li {
    line-height: 1.6;
  }
  ul {
    list-style: none;
    padding: 0;
  }
  li {
    margin: 0.4rem 0;
  }
  strong {
    color: #ffd166;
  }
  .motto {
    text-align: center;
    margin-top: 1.5rem;
    font-style: italic;
    color: #ccc;
    opacity: 0.9;
  }
  footer {
    text-align: center;
    font-size: 0.9rem;
    color: #ddd;
    padding: 1rem;
    background: rgba(0,0,0,0.4);
  }
</style>
</head>
<body>
<header>
  <h1>Expedition 33</h1>
  <p>Mission Log #E33-00</p>
</header>

<div class="container">
  <h2>Mission Brief</h2>
  <p>Expedition 33 is a digital exploration led by <strong>Lune</strong>, <strong>Sciel</strong>, and <strong>Gustave</strong>.  
     Together, they traverse the unknown layers of the Paintress system — seeking order within chaos.</p>

  <h2>Active Nodes</h2>
  <ul>
    <li><strong>Lune</strong> — “When one falls, we continue.”</li>
    <li><strong>Sciel</strong> — “Tomorrow comes.”</li>
    <li><strong>Gustave</strong> — “For those who come after. Right?”</li>
  </ul>

  <h2>Ports</h2>
  <ul>
    <li>Lune: Port <strong>8000</strong></li>
    <li>Sciel: Port <strong>8100</strong></li>
    <li>Gustave: Port <strong>8200</strong></li>
  </ul>

  <div class="motto">
    “Despite the odds, Expedition 33 marches forward.”
  </div>
</div>

<footer>
  © 2025 Expedition 33 — For Those Who Come After
</footer>
</body>
</html>
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
