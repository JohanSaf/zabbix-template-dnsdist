# Zabbix Template: dnsdist

Based on [frei-style/zabbix-powerdns-dnsdist-template](https://github.com/frei-style/zabbix-powerdns-dnsdist-template).

Tested with Zabbix 6.0.12 and dnsdist 1.8.0.

## Installation

Generate a password hash:
```
$ dnsdist -c
> hashPassword('changeme')
$scrypt$ln=10,p=1,r=8$kEEUvPsb05DU8C5U7/1TpA==$nyolI7rQRNaJVYF9ty8qw3I3XbIvcqoeUvoKcvousdk=
```

Enable the [dnsdist webserver](https://dnsdist.org/guides/webserver.html):
```
webserver('127.0.0.1:8083')
setWebserverConfig({password='hash_from_above', apiKey='hash_from_above'})
```

Assign the template to the host and configure these macros to match your setup:
```
{$DNSDIST.APIKEY}
{$DNSDIST.WEBSERVER.IP}
{$DNSDIST.WEBSERVER.PORT}
```
