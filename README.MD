## NextCloud – Your Own Cloud Storage

## FIXES  
  ## Database “READ COMMITTED” transaction isolation level
    ## Change your "/etc/mysql/my.cnf"
    # docker exec -it mariadb bash
    # [mysqld]
    # ...
    # transaction_isolation = READ-COMMITTED
    # binlog_format = ROW
    # ...
 
  ## To fix "bigint" issue:
    # docker exec -it -u root nextcloud "sudo -u www-data php occ db:convert-filecache-bigint --no-interaction"
  
  ## Suggested to create NextCloud database using MariaDB
    # docker exec -it mariadb mysql -uroot -p
    # CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
    # CREATE DATABASE IF NOT EXISTS nextcloud;
    # GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES ON nextcloud.* TO 'username'@'localhost' IDENTIFIED BY 'password';
    # FLUSH privileges;
    
  ## When signing in under Storage & database select MySQL/MariaDB and enter:
    # Database user: your db user (nextcloud)
    # Database password: your db password (<password>)
    # Database name: your db name (nextcloud)
    # localhost: mariadb:3306
 
  # Redis setup in config.php: (Optional)
    # 'memcache.local' => '\OC\Memcache\APCu',
    # 'memcache.distributed' => '\OC\Memcache\Redis',
    # 'memcache.locking' => '\OC\Memcache\Redis',
    # 'redis' => array(
    #     'host' => 'redis',
    #     'port' => 6379,
    # ),
