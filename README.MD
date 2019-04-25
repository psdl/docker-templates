## NextCloud – Your Own Cloud Storage
  ## Suggested to create NextCloud database using MariaDB
    # docker exec -it mariadb mysql -uroot -p
    # CREATE DATABASE nextcloud CHARACTER SET = utf8mb4 COLLATE = utf8mb4_general_ci;
    # GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'nextcloud.traefik_proxy'IDENTIFIED BY '<password>';
    # FLUSH PRIVILEGES;
    # exit
  ## When signing in under Storage & database select MySQL/MariaDB and enter:
    # Database user: your db user (nextcloud)
    # Database password: your db password (<password>)
    # Database name: your db name (nextcloud)
    # localhost: mariadb:3306
 
  ## To fix "bigint" issue:
    # docker exec -it nextcloud sh
    # sudo -u abc php /config/www/nextcloud/occ db:convert-filecache-bigint
    # exit
 
  # Redis setup in config.php: (Optional)
    # 'memcache.local' => '\OC\Memcache\APCu',
    # 'memcache.distributed' => '\OC\Memcache\Redis',
    # 'memcache.locking' => '\OC\Memcache\Redis',
    # 'redis' => array(
    #     'host' => 'redis',
    #     'port' => 6379,
    # ),
