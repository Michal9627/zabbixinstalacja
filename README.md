Konfiguracja Zabbixa:

Konfiguracja bazy danej 

# mysql -uroot -p
password
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;

Po tym jak zrobicie baze danych wpisujecie taką komendę:

# zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix(pojawi się po tym żeby wpisać hasło do bazy danej i wpisujemy jakie ustawiliśmy)

Logujemy się do bazy danej i usuwamy funkcję crators komendą: 
# mysql -uroot -p
password
mysql> set global log_bin_trust_function_creators = 0;
mysql> quit;

wpisujemy komendę 
nano /etc/zabbix/zabbix_server.conf

Potem szyukamy sentensji DBPassword=password i zmieniamy ją 

Jak to zrobimy należy wpisać dwie komendy będzie drugi plik startzabbix.sh
