# BASO-04-20-pr-2
Используя intitle:"forum" inurl:http after:2019, я взял для примера http://loyalty-world.ru

Для определения IP использовал команды ping и nslookup в консоли , а также приложение wireshark.

<a href="https://ibb.co/0y4Yjtm"><img src="https://i.ibb.co/whGpNsB/2-ip-ping.png" alt="2-ip-ping" border="0"></a>

<a href="https://ibb.co/tJGgmZ1"><img src="https://i.ibb.co/4Vqzms0/2-pi-nslookup.png" alt="2-pi-nslookup" border="0"></a>

<a href="https://ibb.co/hsJVkNp"><img src="https://i.ibb.co/D4HQNF3/2-ip-wireshark.png" alt="2-ip-wireshark" border="0"></a>

Затем  использую команду nslookup с доп.опциями -query=mx, soa, nx; type=any и ввожу их в коммандную строку.

Первую команду я использовал -query=mx и сеё помощью узнал , что loyalty-world.ru имеет только один почтовый сервер  mail-s19.1gb.ru

<a href="https://ibb.co/p1rnFD5"><img src="https://i.ibb.co/8m4XZ3t/2-nslookup-1.png" alt="2-nslookup-1" border="0"></a>

Следующая команда которую я использовал была -type=any ,с ею помощью я нашёл  все записи о DNS для нашего домена.

<a href="https://ibb.co/6RZ5HqQ"><img src="https://i.ibb.co/RpSW3J8/2-nslookup-2.png" alt="2-nslookup-2" border="0"></a>

Также я использовал -query=soa , с её помощью я узнал всю информацию о доменной зоне.

<a href="https://ibb.co/P5Dh8WB"><img src="https://i.ibb.co/VvwS8CX/2-nslookup-3.png" alt="2-nslookup-3" border="0"></a>

Последняя команда , которую я использовал, была -query=nx , она ничем не отличается просто от  nslookup.

<a href="https://ibb.co/Z8CXcwS"><img src="https://i.ibb.co/2tBhcLS/2-nslookup-4-png.png" alt="2-nslookup-4-png" border="0"></a>

Следующим пунктоя я изучал трафик с сайта.Для этого я использовал программу wirewshark и фильтры: 
ip.src==(((ip))), ip.dst;ip.addr, udp.src, arp.src.hw_mac, eth.dst, eth.src

1)ip.src=="ip" перехватывает трафик прешедшего с айпи (source -> destination)

<a href="https://ibb.co/zSwsmYx"><img src="https://i.ibb.co/K9H65kh/2-ip-src.png" alt="2-ip-src" border="0"></a>

2)ip.dst=="ip" тоже самое, только наоборот, перехватывает трафик от моего айпи до айпи сайта (destination -> source)

<a href="https://ibb.co/w0kfqnJ"><img src="https://i.ibb.co/SsjzgkQ/2-ip-dst.png" alt="2-ip-dst" border="0"></a>

C помощью этих фильтров можно понять какие протоколы использует сайт (HTTP / TCP) и какие порты используются для подключения к нему.

3)ip.addr используется дял того , чтобы увидеть пакеты в независимости от направления трафика.

<a href="https://ibb.co/tYXKws3"><img src="https://i.ibb.co/6DBwcPN/2-ip-addr.png" alt="2-ip-addr" border="0"></a>

4)udp.src не заработала.

5)arp.src.hw_mac фильтр arp , только с доп.фильтрацией по mac адресу.

<a href="https://ibb.co/m0hCwXj"><img src="https://i.ibb.co/ZSc6PYj/2-arp.png" alt="2-arp" border="0"></a>

6)eth.src фильтрует все пакеты по маку.

<a href="https://ibb.co/SnRY2mW"><img src="https://i.ibb.co/58Bpdjt/2-eth-scr.png" alt="2-eth-scr" border="0"></a>

7)eth.dst тоже самое , что и eth.scr.

<a href="https://ibb.co/Jd0nMr9"><img src="https://i.ibb.co/PY3xf1d/2-eth-dst.png" alt="2-eth-dst" border="0"></a>





