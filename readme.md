

# Instructions
## Build
Compose in CMD or other Terminal at the root directory of the folder
``` docker compose up -d ```

## Execute
Attach to the clientmac to run the following commands
``` docker attach clientmac ```
1. Validate your internal IP Address Allocated to ClientMac
``` ip addr show ```

2. Validate the reverse proxy
```
curl handler1:80 #Restricted
curl handler1:81 #Allowed
```

## Update
Manipulate the Handler Nginx Config (use a new terminal)
```
docker exec -it handler1 sh -c "echo 'allow 172.21.0.2;' > '/var/www-allow/board_a_allow.conf' && service nginx reload"
docker exec -it handler1 sh -c "echo 'deny all;' > '/var/www-allow/board_a_allow.conf' && service nginx reload"
```