# kong
Kong for Canopy

### Installation instructions

1. Clone this repository:
   ```sh
$ git clone https://github.com/CanopyCloud/cip-kong.git cip-kong
```

2. Start Cassandra:
   ```sh
$ sudo docker run -p 9042:9042 -d --name cassandra mashape/cassandra
```

3. Start Kong:
   ```sh
$ sudo docker run -d \
    -v /cip-kong \
    -p 8000:8000 \
    -p 8001:8001 \
    --name kong \
    --link cassandra:cassandra \
    mashape/kong
```

### Testing

1. Add your "/info" API for canopycloud/microservice-nodejs:
   ```sh
$ curl -i -X POST \
 --url http://localhost:8001/apis/ \
 --data 'name=info' \
 --data 'target_url=http://localhost:3000/info' \
 --data 'public_dns=info'
```

2. Check the API:
   ```sh
$ curl -i -X GET \
 --url http://localhost:8000/ \
 --header 'Host: info'
```
