# apache-docker-container-htaccess

Simple Apache Docker container with a straightforward `.htaccess` file.

## Files

1. [Dockerfile](Dockerfile) - Create the server with `a2enmod rewrite` enabled. Server created is the simple `php:7.2-apache` server; _I might update at some point in time in the future._
2. [docker-compose.yml](docker-compose.yml) - Server built diagram - on `127.0.0.1:80:80`
3. [.htaccess](.htaccess) - Simple `.htaccess` file with `RewriteEngine on` and a single `RewriteRule`.

## How to use

1. _(optional)_ Set up a host (default: `http://localhost`)
2. Open Terminal
3. Navigate to root folder with Docker files
4. Run `docker-compose up --build`
5. Open new Terminal window/tab
6. Run `curl -I http://localhost/hello-world`
7. Confirm response is a 301-Permanent redirect to `https://example.com/`

## Example

### Input

```
RewriteRule hello-world https://example.com/ [R=301,QSD,L]
```

### Output

```
$ curl -I http://localhost/hello-world
HTTP/1.1 301 Moved Permanently
Date: Thu, 27 Oct 2022 08:23:20 GMT
Server: Apache/2.4.38 (Debian)
Location: https://example.com/
Content-Type: text/html; charset=iso-8859-1
```

## Notes
* When changing the `.htaccess` file, there is no need to restart the server - the changes should take effect immediately on the running container.