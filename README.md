# nth-mariadb

Hướng dẫn cài đặt MariaDB sử dụng Podman.

https://github.com/MariaDB/mariadb-docker

Tạo Volumn trên podman để lưu dữ liệu:

```bash
podman volume create mariadb-data

podman volume create mariadb-conf

podman volume create mariadb-backup
```

Tạo network nếu chưa có:

```bash
podman network create nth
```

Chạy MariaDB

```bash
podman run -d \
  --name mariadb \
  --network nth \
  --restart=always \
  -e MYSQL_ROOT_PASSWORD=123123 \
  -e MYSQL_USER=nth \
  -e MYSQL_PASSWORD=123123 \
  -e MYSQL_DATABASE=nth \
  -v mariadb-data:/var/lib/mysql:Z \
  -v mariadb-conf/my.cnf:/etc/mysql/my.cnf:Z \
  docker.io/library/mariadb:10.11

```

