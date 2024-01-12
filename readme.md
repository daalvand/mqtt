# Document



## add user and it will prompt for password
```shell
docker compose exec mqtt mosquitto_passwd -c /mosquitto/config/pwfile <user-to-add>
```
## delete user command format
```shell
docker compose exec mqtt mosquitto_passwd -D /mosquitto/config/pwfile <user-to-delete>
```

##  Subscribe from a topic ('hello/topic')

### Without authentication
```shell
docker compose exec mqtt mosquitto_sub -v -t 'hello/topic' -h localhost
```
### With authentication
```shell
docker compose exec mqtt mosquitto_sub -v -t 'hello/topic' -h localhost -u <user> -P <password>
```
### Alternate way in url format
### Format => mqtt(s)://[username[:password]@]host[:port]/topic
```shell
docker compose exec mqtt mosquitto_sub -v -L  mqtt://<user>:<password>@localhost/test/topic
```
## Publish to a topic ('hello/topic')

### Without authentication
```shell
docker compose exec mqtt mosquitto_pub -t 'hello/topic' -h localhost -m 'hello MQTT' 
```
### With authentication
```shell
docker compose exec mqtt mosquitto_pub -t 'hello/topic' -h localhost -u <user> -P <password> -m 'hello MQTT'
```
### Alternate way in url format 
### Format => mqtt(s)://[username[:password]@]host[:port]/topic
```shell
docker compose exec mqtt mosquitto_pub -L mqtt://<user>:<password>@localhost/test/topic -m 'hello MQTT'
```
