# Wireguard

Обновление OC
```
apt update -y && apt upgrade -y
```
Установка необходимого софта
```
apt install nano -y && apt install mc -y && apt install htop -y && apt install git -y
```
Установка Docker
```
curl https://get.docker.com -o install.sh && sh install.sh
```
```
systemctl enable docker.service
```
```
systemctl enable docker
```
```
usermod -aG docker $USER
```
Клонирование репозитория
```
git clone https://github.com/scerka-soft/wireguard.git
```
Переходим в папку wireguard
```
cd wireguard
```
Редактируем docker-compose.yml
```
nano docker-compose.yml
```

Изменяем 2 значения (***CTRL+S***, ***CTRL+X*** для сохранения и выхода)
```
- PASSWORD_HASH=$$2y$$10$$hBCoykrB95WSzuV4fafBzOHWKu9sbyVa34GJr8VV5R/pIelfEMYyG (пароль для UI 123456 по умолчанию)
- WG_HOST=10.0.2.15 (Поменять на свой ip4)
```
[Генератор пароля](https://bcrypt-generator.com/), после генерации там где $ добавить ещё один $, пример ```$2a$12$ldlVdG4gG0``` -> ```$$2a$$12$$ldlVdG4gG0```
Запуск wireguard
```
docker compose up --detach
```

**Готово!** Переходим в браузер вводим свой ip4:8080 переходим на страницу, вводим пароль из docker-compose.yml и добавляем устройства.