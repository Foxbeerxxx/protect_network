# Домашнее задание к занятию "`Защита сети`" - `Татаринцев Алексей`


---

### Задание 1

1. `Подготовка системы`
```
Подготовка к выполнению заданий
Подготовка защищаемой системы: ( 192.168.1.10)
- установите Suricata,
- установите Fail2Ban.
Подготовка системы злоумышленника:( 192.168.1.100) установите nmap и thc-hydra либо скачайте и установите Kali linux.
Обе системы должны находится в одной подсети.
```

2. `Задание 1`
```
Проведите разведку системы и определите, какие сетевые службы запущены на защищаемой системе:

sudo nmap -sA 192.168.1.10

sudo nmap -sT 192.168.1.10

sudo nmap -sS 192.168.1.10

sudo nmap -sV 192.168.1.10
```
По желанию можете поэкспериментировать с опциями: https://nmap.org/man/ru/man-briefoptions.html.


![1](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img1.png)`

![2](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img2.png)`

3. `Поведение suricata при сканировании nmap`
```
sudo nmap -sA 192.168.1.10

sudo nmap -sT 192.168.1.10

sudo nmap -sS 192.168.1.10

sudo nmap -sV 192.168.1.10

```

![3](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img3.png)`

4. `Fail2ban на nmap сканирование не реагирует`



---

### Задание 2

1. `Подготавливаю словари user.txt и pass.txt`
![5](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img5.png)`

![6](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img6.png)`


2. ` отключаю сервис fail2ban и пробую подбирать пароль и логин через hydra`
```
hydra -L user.txt -P pass.txt 192.168.1.140 ssh
```
3. `Смотрим лог`
![4](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img4.png)`

3. `Затем включаем сервис и пробуем подобрать пароль по ssh`
4. `Проверяем лог file2ban`

![7](https://github.com/Foxbeerxxx/protect_network/blob/main/img/img7.png)`
4. `Сервис блокирует атаку`