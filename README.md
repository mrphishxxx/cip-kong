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
    mashape/kong
```
