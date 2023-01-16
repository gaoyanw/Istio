# set up an envoy reverse proxy
## Requirement
Set up a reverse proxy that can receive a standard http requrest
if the request begins with "/google", send the request to www.google.com
if the request begins with "/vpp", send the request to virtualpairprogramming.com

## Steps
1. start docker on mac
2. build the image
```
docker image build -t envoy-demo .
```
3. run the image
```

docker container run -d -p 10001:10000 -p 9902:9901 envoy-demo
```

4. get the container information
```
docker container ls
CONTAINER ID   IMAGE           COMMAND                  CREATED          STATUS          PORTS                                              NAMES
7bcb9925666c   envoy-demo      "/docker-entrypoint.…"   13 seconds ago   Up 11 seconds   0.0.0.0:9902->9901/tcp, 0.0.0.0:10001->10000/tcp   lucid_germain
```

5. send traffic to envoy visit 0.0.0.0:10001/google and 0.0.0.0:10001:vpp
   
## Notes
1. port 10000 is randomly selected
2. port 9901 is reserved for envoy admin panel



