```
nano /etc/bind/named.conf.local
```

```
options {
    directory "/etc/bind";
    recursion no;
    listen-on { any; };
    allow-query { any; };
};

zone "lune33.com" {
    type slave;
    file "slaves/db.lune33.com"; // lokasi file db
    masters { 10.24.3.1; }; //ip dns master
};

zone "sciel33.com" {
    type slave;
    file "slaves/db.sciel33.com"; // lokasi file db
    masters { 10.24.3.1; }; //ip dns master
};

zone "gustave33.com" {
    type slave;
    file "slaves/db.gustave33.com"; // lokasi file db
    masters { 10.24.3.1; }; //ip dns master
};
```

```
mkdir -p /etc/bind/slaves
```

```
nano /etc/bind/slaves/db.lune33.com
```

```
$TTL 86400
@ IN SOA lune33.com. root.lune33.com. (
    4 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     lune33.com.
@   IN A      10.24.2.1
```

```
nano /etc/bind/slaves/db.sciel33.com
```

```
$TTL 86400
@ IN SOA sciel33.com. root.sciel33.com. (
    5 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     sciel33.com.
@   IN A      10.24.2.2
```

```
nano /etc/bind/slaves/db.gustave33.com
```

```
$TTL 86400
@ IN SOA gustave33.com. root.gustave33.com. (
    6 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     gustave33.com.
@   IN A      10.24.2.3
```

```
mkdir /etc/bind/delegasi
```

```
cp /etc/bind/slaves/db.gustave33.com /etc/bind/delegasi/expedition.gustave33.com
```

```
nano /etc/bind/delegasi/expedition.gustave33.com
```

```
$TTL 86400
@ IN SOA gustave33.com. root.gustave33.com. (
    6 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@           IN NS     gustave33.com.
@           IN A      10.24.2.3
expedition  IN A      10.24.2.3
```

```
named -g -c /etc/bind/named.conf.local
```
