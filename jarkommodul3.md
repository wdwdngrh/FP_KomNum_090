# Renoir, dns master

```
nano /etc/bind/named.conf.local
```

```
options {
  directory "/etc/bind";
  listen-on { any; };
  allow-query { any; };
  dnssec-validation no;
};

zone "lune33.com" {
    type master;
    file "db.lune33.com";
    also-notify { 10.24.3.2; };
    allow-transfer { 10.24.3.2; };
};

zone "sciel33.com" {
    type master;
    file "db.sciel33.com";
    also-notify { 10.24.3.2; };
    allow-transfer { 10.24.3.2; };
};

zone "gustave33.com" {
    type master;
    file "db.gustave33.com";
    also-notify { 10.24.3.2; };
    allow-transfer { 10.24.3.2; };
};
```

`nano /etc/bind/db.lune33.com`

```
$TTL 86400
@ IN SOA ns1.lune33.com. root.lune33.com. (
    1 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     ns1.lune33.com.
@   IN NS     ns2.lune33.com.

@   IN A      10.24.2.1
ns1 IN A      10.24.3.1
ns2 IN A      10.24.3.2
www IN A      10.24.2.1
exp IN CNAME  lune33.com.
```

`nano /etc/bind/db.sciel33.com`

```
$TTL 86400
@ IN SOA ns1.sciel33.com. root.sciel33.com. (
    2 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     ns1.sciel33.com.
@   IN NS     ns2.sciel33.com.

@   IN A      10.24.2.2
ns1 IN A      10.24.3.1
ns2 IN A      10.24.3.2
www IN A      10.24.2.2
exp IN CNAME  sciel33.com.
```

`nano /etc/bind/db.gustave33.com`

```
$TTL 86400
@ IN SOA ns1.gustave33.com. root.gustave33.com. (
    3 ; serial
    3600 ; refresh
    1800 ; retry
    604800 ; expire
    86400 ) ; minimum

@   IN NS     ns1.gustave33.com.
@   IN NS     ns2.gustave33.com.

@           IN A      10.24.2.3
ns1         IN A      10.24.3.1
ns2         IN A      10.24.3.2
www         IN A      10.24.2.3
expedition  IN CNAME  gustave.com.
```

`named -4 -g -c /etc/bind/named.conf.local`
