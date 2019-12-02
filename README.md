# DockerStartScripts
Just a few start scripts stored here for referance.

Proxy Containers (https://github.com/jwilder/nginx-proxy)
docker run -d \
    --name nginx-proxy-http \
    -p 80:80 \
    -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy
    
docker run -d \
    --name nginx-proxy-https \
    -p 443:443 \
    -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy
