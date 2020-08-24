docker_kdc
==========

Minimalistic Kerberos Key Distribution Center Docker image

docker hub
----------

ilejn/kdc

Usage
-----

It is assumed that all initialization stuff is put in config.sh via _volume_ facilities

config.sh example
-----------------

Can be found in example directory is rather complex one,
several keytabs are created during start up.


docker_compose example
----------------------

``` yaml
  a_kerberized_server:
    ...
    volumes:
        - host_path_to_keytabs:/server/secrets
  kdc:
    image: ilejn/kdc:latest
    hostname: kafka_kerberos
    volumes:
        - host_path_to_keytabs:/tmp/keytab
        - /dev/urandom:/dev/random
    ports: [88, 749]
```
