## Upute za izradu laravel aplikacije (lokalno)

#### 1. Pokrenuti laragon
#### 2. Kreirati laravel aplikaciju
Desnim klikom na laragon sučelje odabrati kreiranje nove Laravel aplikacije

ili

Koristeći composer putem terminala  
`composer create-project --prefer-dist laravel/laravel ui_projekt`

#### 3. Kreirati bazu podataka
Koristeći laragon heidi alat, kreirati novu bazu podataka.  
Ukoliko ste projekt izradili preko laragon sučelja, baza se automatski kreira.

#### 4. Postaviti okruženje (.env)
Unutar .env datoteke postaviti okruženje i podatke za pristup bazi podataka

DB_DATABASE=ui2024 // Ime vase baze  
DB_USERNAME=root  
DB_PASSWORD=

#### NPM
npm install  
npm run dev // Dev za debug nacin rada  
ili  
npm run watch // automatski osvjezava promjene css/js

**Aplikacija je lokalno dostupna na ui2024.test**

#### Kreiranje baze podataka
    php artisan migrate

DROP cijele baze i ponovno pokretanje migracija! Oprez!

    php artisan migrate:fresh

#### Kreiranje modela
    php artisan make:model Car -mcr --api

#### Uređivanje migracije
File database/migrations/timestamp_create_model_table.php

Ponovno pokrenuti migraciju kako bi se odrazile promjene
php artisan migrate

#### Dodavanje polja u bazi u fillable
Kako bi se polja mogla upisivati kroz Eloquent ORM metode, potrebno je omoguciti da polja u bazi budu tzv. mass assignable.

To postižemo override-om $fillable svojstva unutar našeg modela npr.

app/models/Car.php

        protected $fillable = ['manufacturer', 'year', 'model_name', 'color'];



#### PHP Laravel tinker
Ulaskom u tinker otvara se php shell sa laravel okruzenjem.
Služi za testiranje pojedinih naredbenih linija koda.

    php artisan tinker

#### CRUD modela u tinker-u

CREATE

     Car::create(['manufacturer'=>'Audi', 'model_name'=>'A6', 'year'=>2020])

READ

Svi modeli (array)

    Car::all()

Jedan model po ID (objekt)

    Car::find(1)

UPDATE

    $car = Car::find(1);
    $car->model_name = 'A4';
    $car->save();

DELETE

    $car = Car::find(1);
    $car->delete();

## Upute za postavljanje projekta na studentski server


#### 1. Prijava na studentski poslužitelj

    Host: studenti.sum.ba

    Korisničko ime: uiXXYYYY

    Lozinka: csdigitalYYYY

**XX** broj grupe (01, 02, 03...)

**YYYY** akademska godina

<br>

#### 2. Unutar Vašeg foldera klonirati repozitorij s githuba
    git clone https://github.com/RobertRozic/ui2024.git


#### 3. Napraviti simbolički link sa **public** direktorij-a u laravel projektu na **backend** folder na posluzitelj

    ln -s /home/uiXXYYYY/ime-projekta/public/ /home/uiXXYYYY/public

#### 4. Pozicionirati se u folder projekta
    cd ~/ime-projekta

#### 5. Instalirati composer dependency-je
    composer install

#### 6. Podesiti .env na poslužitelju
Primjer kopiramo u .env file

    cp .env.example .env

Podesimo bazu

    DB_DATABASE=uiXXYYYY
    DB_USERNAME=uiiXXYYYY
    DB_PASSWORD=csdigitalYYYY

Generiramo key aplikacije

    php artisan key:generate

#### 7. Podesiti permisije
    chgrp -R www-data storage bootstrap/cache
    chmod -R ug+rwx storage bootstrap/cache

### Backend aplikacije je dostupan na linku
    http://uiXXYYY.studenti.sum.ba


### Baza podataka
Na studentskom poslužitelju svaka grupa ima MySql bazu.

Pristupni podaci su (.env laravel konfiguracija):  
DB_HOST=localhost (localhost na samom poslužitelju)  
DB_DATABASE=uiXXYYYY    
DB_USERNAME=uiXXYYYY  
DB_PASSWORD=csdigitalYYYY

Bazi podataka možete pristupiti putem phpmyadmin-a instaliranog na poslužitelju.  
Putem PhpMyAdmina možete raditi import podataka koje imate na lokalnoj bazi.

[PHPMyAdmin](https://studenti.sum.ba/phpmyadmin)

### Ažuriranje projekta
Nakon pristupa folderu u kojem se nalazi vaš projekt, koristite naredbu
####
    git pull
Ova naredba povlači sve promjene koje ste postavili na javni github repozitorij


### [Video lekcija](https://www.youtube.com/watch?v=R4_Pqt3lhPk)

Ukoliko imate problema s postavljanjem, javite se na email `robert.rozic@fpmoz.sum.ba`


## Osnovne naredbe u linuxu
* **pwd** - Ispis putanje trenutnog foldera u kojemu se nalazimo (**p**rint **w**ork **d**irectory)

`pwd`  
`/home/ui002024`

* **cd** - Promjena direktorija (**c**hange **d**irectory)

`cd public`

Vraćanje u prethodni direktorij

`cd ..`

* **mkdir** - Kreiranje direktorija (**m**ake **d**irectory)

`mkdir test`

* **touch** - Kreiranje datoteke

`touch test.txt`

* **nano** - Ugrađeni tekstualni editor

`nano test.txt`

Za izlazak iz editora koristi se CTRL+X, zatim editor pita za spremanje datoteke.

Pritisnite y (za da) ili n (za ne).

* **ln -s** - Kreiranje simboličkog linka

`ln -s izvor odrediste`

Brisanje datoteke/direktorija

`rm -rf public`


