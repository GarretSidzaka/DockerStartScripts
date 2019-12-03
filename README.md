# DockerStartScripts
Just a few start scripts stored here for referance.

Proxy Containers (https://github.com/jwilder/nginx-proxy)
`docker run -d \
    --name nginx-proxy-http \
    -p 80:80 \
    -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy
    
docker run -d \
    --name nginx-proxy-https \
    -p 443:443 \
    -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy`
    
 Encrypted Proxy (https://cloud.google.com/community/tutorials/nginx-reverse-proxy-docker)


    `docker run -d -p 80:80 -p 443:443 \
    --name nginx-proxy \
    -v $HOME/certs:/etc/nginx/certs:ro \
    -v /etc/nginx/vhost.d \
    -v /usr/share/nginx/html \
    -v /var/run/docker.sock:/tmp/docker.sock:ro \
    --label com.github.jrcs.letsencrypt_nginx_proxy_companion.nginx_proxy=true \
    jwilder/nginx-proxy
    
    docker run -d \
    --name nginx-letsencrypt \
    --volumes-from nginx-proxy \
    -v $HOME/certs:/etc/nginx/certs:rw \
    -v /var/run/docker.sock:/var/run/docker.sock:ro \
    jrcs/letsencrypt-nginx-proxy-companion
    
    docker run -d \
    --name site-a \
    -e 'LETSENCRYPT_EMAIL=webmaster@example.com' \
    -e 'LETSENCRYPT_HOST=a.example.com' \
    -e 'VIRTUAL_HOST=a.example.com' nginx
    
    docker run -d \
    --name site-b \
    -e 'LETSENCRYPT_EMAIL=webmaster@example.com' \
    -e 'LETSENCRYPT_HOST=b.example.com' \
    -e 'VIRTUAL_HOST=b.example.com' httpd`
