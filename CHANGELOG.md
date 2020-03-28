# Changelog

## 3.9-0.9.8-0.13.8-RC14 (2020/03/27)

* Fix folder creation

## 3.9-0.9.8-0.13.8-RC13 (2020/01/24)

* Move Nginx temp folders to `/tmp`

## 3.9-0.9.8-0.13.8-RC12 (2020/01/02)

* Use [geoip-updater](https://github.com/crazy-max/geoip-updater) Docker image to download MaxMind's GeoIP2 databases

## 3.9-0.9.8-0.13.8-RC11 (2019/12/07)

* Fix timezone

## 3.9-0.9.8-0.13.8-RC10 (2019/11/23)

* Dedicated container for rtorrent logs

## 3.9-0.9.8-0.13.8-RC9 (2019/11/23)

* `.rtorrent.rc` not taken into account

## 3.9-0.9.8-0.13.8-RC8 (2019/11/22)

* Switch to [s6-overlay](https://github.com/just-containers/s6-overlay/) as a process supervisor
* Add `PUID`/`PGID` vars (#12)
* Do not set defaults if `RU_REMOVE_CORE_PLUGINS` is empty
* Nginx mainline base image

## 3.9-0.9.8-0.13.8-RC7 (2019/10/26)

* Base image update

## 3.9-0.9.8-0.13.8-RC6 (2019/10/25)

* Fix CVE-2019-11043

## 3.9-0.9.8-0.13.8-RC5 (2019/10/17)

* Remove `PUID` / `PGID` vars

## 3.9-0.9.8-0.13.8-RC4 (2019/10/16)

* Switch to GitHub Actions
* :warning: Stop publishing Docker image on Quay
* Move boostrap (default) config for rTorrent to `/etc/rtorrent/.rtlocal.rc`
* :warning: Run as non-root user
* Prevent exposing nginx version
* Set timezone through tzdata

> :warning: **UPGRADE NOTES**
> As the Docker container now runs as a non-root user, you have to first stop the container and change permissions to volumes:
> ```
> docker-compose stop
> chown -R 1000:1000 data/ passwd/
> docker-compose pull
> docker-compose up -d
> ```

## 3.9-0.9.8-0.13.8-RC3 (2019/09/04)

* Create `share/torrents` for ruTorrent

## 3.9-0.9.8-0.13.8-RC2 (2019/08/07)

* Add healthcheck
* Allow directory listing for WebDAV
* Remove php-fpm access log (already mirrored by nginx)

## 3.9-0.9.8-0.13.8-RC1 (2019/07/22)

* ruTorrent 3.9 revision [Novik/ruTorrent@ec8d8f1](https://github.com/Novik/ruTorrent/commit/ec8d8f1887af57793a671258072b59193a5d8d6c)
* rTorrent 0.9.8 and libTorrent 0.13.8
* XMLRPC 01.55.00
* cURL 7.65.3

## 3.9-0.9.7-0.13.7-RC3 (2019/04/28)

* Add `large_client_header_buffers` Nginx config

## 3.9-0.9.7-0.13.7-RC2 (2019/04/15)

* Add `REAL_IP_FROM`, `REAL_IP_HEADER` and `LOG_IP_VAR` environment variables

## 3.9-0.9.7-0.13.7-RC1 (2019/04/09)

* ruTorrent 3.9

## 3.8-0.9.7-0.13.7-RC7 (2019/01/14)

* Add mktorrent for ruTorrent create plugin
* Replace core ruTorrent GeoIP plugin with [GeoIP2 plugin](https://github.com/Micdu70/geoip2-rutorrent)

## 3.8-0.9.7-0.13.7-RC6 (2019/01/09)

* Allow to customize auth basic string (Issue #5)

## 3.8-0.9.7-0.13.7-RC5 (2019/01/08)

* Bind ruTorrent HTTP port to unprivileged port : `8080`
* Fix Nginx WebDAV module version
* Update ruTorrent to Novik/ruTorrent@4d3029c
* Update libs (XMLRPC, Libsig, cURL)

## 3.8-0.9.7-0.13.7-RC4 (2018/12/04)

* Nginx `default.conf` overrides our conf (Issue #1)

## 3.8-0.9.7-0.13.7-RC3 (2018/12/03)

* Based on `nginx:stable-alpine`
* Optimize layers

## 3.8-0.9.7-0.13.7-RC2 (2018/06/26)

* Include path error for custom plugins and themes

## 3.8-0.9.7-0.13.7-RC1 (2018/06/25)

* Add ruTorrent 3.8 web client
* Add option to remove core plugins of ruTorrent (default `erasedata,httprpc`)
* Add a boostrap (default) config for rTorrent in `/etc/.rtlocal.rc`
* Move `/var/rtorrent` to `/data/rtorrent`
* Use Nginx WebDAV module instead of Apache
* Compile Nginx from source for better performance
* Remove Apache2 and implement Nginx WebDAV
* Do not process entrypoint on `htpasswd` command
* Add reverse proxy example with Traefik
* Remove old docker tags `0.9.6-0.13.6` and `0.9.7-0.13.7`
* Do not persist runtime data
* Rename repository `rtorrent-rutorrent` (github and docker hub)

## 0.9.7-0.13.7-RC3 (2018/06/18)

* Force rTorrent process as a daemon through command flag
* Add .rtorrent.rc if not exist

## 0.9.7-0.13.7-RC2 (2018/06/17)

* Move runtime data in `/var/rtorrent/run`
* Enable WebDAV protocol on `downloads/complete` with basic auth

## 0.9.7-0.13.7-RC1 (2018/06/16)

* rTorrent 0.9.7 and libTorrent 0.13.7
* Base image updated to Alpine Linux 3.7
* c-ares 1.14.0
* curl 7.60.0
* Move `RTORRENT_HOME` to `/var/rtorrent`
* XMLRPC through nginx over SCGI socket with basic auth
* Do not expose SCGI port (use a local socket instead)
* Run the rTorrent process as a daemon
* Replace deprecated commands in `.rtorrent.rc`
* Review supervisor config

## 0.9.6-0.13.6-RC1 (2018/01/10)

* Initial version
