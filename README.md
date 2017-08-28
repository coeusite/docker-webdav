# Usage
This is an NGINX WebDAV docker with some basic WebDAV functionality. Its main purpose is in end-to-end test environments to upload files.

Via two environment variables basic authentication can be set:
```
	WEBDAV_USERNAME
	WEBDAV_PASSWORD
```

If either environment variable is missing, basic authentication is removed.

Basic usage:

	docker run -d --name webdav -p 80:80 -v "$PWD":/var/www pooya/webdav

Sample docker-compose:   
     
```yaml
  webdav:
    image: coeusite/docker-webdav
    environment:
        - VIRTUAL_HOST=virtualhost.for.nginx.proxy
        - VIRTUAL_PORT=80
        - VIRTUAL_PROTO=http
        - LETSENCRYPT_HOST=same as VIRTUAL_HOST
        - LETSENCRYPT_EMAIL=your@email	
        - WEBDAV_USERNAME=username
        - WEBDAV_PASSWORD=password
    volumes:
        - ./data:/var/www:rw
 ```	
