# HLstatsX docker & docker-compose

HLstatsX docker file for development etc.


## License

I'm not using HLstatsX's source code, so... MIT!

## Requirements
1. Docker 17.06.0+
2. Docker-Compose 3.3+
3. GNU/Linux (macOS & Windows NT-based systems not tested)

# How to

1. Clone this repo:
```bash
git clone https://github.com/techiedesu/HLstatsX-docker.git
```

2. Enter into cloned directory and clone hlstatsx: 
```bash
cd HLstatsX-docker
git clone https://github.com/nikooo777/hlstatsx-community-edition.git
```

3. Create symlink
```bash
ln -s  $("pwd")/hlstatsx-community-edition/web $("pwd")/statsx_content/www
```

4. Create config file for hlstatsx or copy existing `sample.config.php`
```bash
sed -i '48s/.*/define("DB_USER", "root");/' statsx_content/www/config.php
sed -i '51s/.*/define("DB_PASS", "root");/' statsx_content/www/config.php
sed -i '54s/.*/define("DB_NAME", "hlstatsx");/' statsx_content/www/config.php
```
Otherwise, you can manually config file and use mysql connection data:
```
User: root
Password: hlstatsx
Database: hlstatsx 
```

5. Run docker-compose
```bash
docker-compose up -d
```

5. Setup hlstatsx database

```bash
cat hlstatsx-community-edition/sql/install.sql | docker exec -i mysql mysql -uroot -proot -Dhlstatsx
```

6. Open http://localhost:8050/

