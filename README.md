#### Autoryzacja

- Aws Maszyna
- sprawdzamy dostęp

#### Instalacja oprogramowania

- Wordpress
- Serwer HTTP
- plik wp
- serwer bazy danych
- Interpreter php
- stworzenie bazy
- pliki konfiguracyjne



#### Maszyn AWS i Autoryzacja

Naszym celem jest stworzenie maszyny na AWS i uzyskanie do niej dostępu.

1. Stworzenie maszyna na AWS.

2. Uzyskanie dostępu do naszej instancji.

   ```
   ec2-user@adresIP -i ./id_student
   Podajemy frazę: student1
   ```



#### Instalacja oprogramowania

Naszym celem jest zainstalowanie i skonfigurowanie wszystkich niezbędnych rzeczy do działania wordpress.

- HTTP server (apache)
- PHP
- Maria DB (serwer bazy danych)
- Konfiguracja w plikach
- Konfiguracja DB i HTTP



##### Dodanie bazy danych 

1. Wchodzimy na stronę "MariaDB Repositories".
2. W naszym przypadku wybieramy dystrybucję "CentOS 7 (x86_64)", wersja serwera: "10.5"
3. Przechodzimy do folderu "/etc/yum.repos.d"
4. Tworzymy plik "sudo vi MariaDB.repo" i wklejamy kod wygenerowany w kroku 2.
5. Instalujemy serwer bazy danych komendą "sudo yum install MariaDB-server MariaDB-client"
6. Startujemy usługę "sudo systemctl start mariadb"
7. Łączymy się z serwerem użytkownikiem root: "sudo mysql -u root"
8. Tworzymy bazę danych "create database blog"
9. Tworzymy użytkownika "create user bloger identified by ''haslo"
10. Przyznajemy dostępy użytkownikowi "grant all privileges on blog.* to 'bloger'@localhost identified by 'haslo';"
11. Wychodzimy: "\q"



##### PHP

1. Wchodzimy na stronę "EPEL AWS"
2. Instalacja paczki: "sudo yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm"
3. Wchodzimy na stronę "Remi Repo"
4. Instalujemy paczkę "yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm"
5. Instalujemy pakiety: "sudo yum install php74 php74-php"



##### HTTP

1. Instalujemy moduł: "sudo yum install httpd"
2. Instalujemy Wordpress "wget https://wordpress.org/latest.zip"
3. Wypakowujemy "unzip latest.zip"
4. Przenosimy zawartoś pliku wordpress do domyślnego katalogu html: "sudo mv Wordpress/* /var/www/html/"
5. Przechodzimy do "/var/www/html/"
6. Kopiujemy plik konfiguracyjny: "sudo cp wp-config-sample.php wp-config.php"
7. Edytujemy: "sudo vi wp-config.php"
8. Wypełniamy istotne informacje: 
   1. DB_NAME - blog
   2. DB_USER -  bloger
   3. DB_PASSWORD - haslo
   4. DB_HOST - localhost
9. Instalacja pakietów: "sudo yum install php74-php-mysqlnd php74-php-pecl-mysql"
