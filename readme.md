

# Instructions
## build

``` docker compose up -d ```

## execute
``` docker attach clientmac ```
Validate your internal IP Address Allocated to ClientMac
``` ip addr show ```

Validate the reverse proxy
```
curl handler1:80 #Restricted
curl handler1:81 #Allowed
```

Manipulate the Handler Nginx Config (use a new terminal)
```
docker exec -it handler1 sh -c "echo 'allow 172.21.0.2;' > '/var/www-allow/board_a_allow.conf' && service nginx reload"
docker exec -it handler1 sh -c "echo 'deny all;' > '/var/www-allow/board_a_allow.conf' && service nginx reload"
```