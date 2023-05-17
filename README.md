# Projekt-JDD

Grupa w składzie:
- Jerzy Tarasiewicz
- Damian Tomala
- Dorota Gliniak

# Zadanie numer 1:

Do zadania 1 wykorzystane narzędzia:
1. hash-identifier
2. hashcat

Do zadania 1 - 1/3, 2/3, 3/3 pkt.1-4, wykonaliśmy następujące czynności:

1. W konsoli uruchomiliśmy program 'hash-dentifier' - poleceniem: hash-dentifier
2. W wyżej wymienionym programie wkleiliśmy hash'e przyporządkowane do odpowiednich punktów.
3. Jako wynik otrzymaliśmy informację jaki typ algorytmu został użyty.
4. W konsoli używając 'hashcat' złamaliśmy hasło metodą brute-force.
   Użyliśmy następujących znaczników:
   - '-a 3'    - co oznacza atack mode 3 (brute force)
   - '-m 0'    - co oznacza algorytm 0 (algorytm MD5)
   - '-m 100'  - co oznacza algorytm 100 (algorytm SHA-1)
   - '-m 1700' - co oznacza algorytm 1700 (algorytm SHA-512)
   - '--show'  - użycie tego znacznika na końcu polecenia wyświetla tylko hasło
  W Projekcie 2 zostały użyte tylko w/w algorytmy.
5. Jako wynik otrzymaliśmy informację, że hasło zostało złamane z adnotacją jakie to hasło.
6. Do każdej z w/w czynności wykonaliśmy screenshoty.
7. Do zadania 3/3 ze względu na brak możliwości skorzystania z GPU użyliśmy metody słownikowej z zastosowaniem pliku rockyou.txt.

Koniec zadania nr 1.

## Wyniki: 

## 1/3
1: 1234, MD5 (3)

2: 4121, SHA1 (100)

3: 6969, SHA-512 (1700)

4: 0, SHA-512 (1700)

## 2/3 

Łamanie haseł (met. brute-force)

1: sda, SHA-512 (1700)

2: Asia, SHA-512 (1700)

## 3/3 

Zadanie niewykonalne ze wzglęgu na szyfrowanie https.

Sugerowane rozwiązanie na www.edu.pl
Szczegółu wybranego pakietu sieciowego
Niewykonalne w przypadku stron szyfrowanych SSL (protokół HTTPS) - Sugerowane rozwiązanie przez: https://haker.edu.pl/2015/10/14/wireshark-sniffer-i-tcpdump-podsluch/
W tym przypadku zręczny cyberprzestępca i tak sobie może poradzić uruchamiając na swoim komputerze stronę phishingową i wykorzystując atak MITM połączony z DNS poisoning lub wykorzystując takie narzędzia hakerskie jak SSLstrip.

Załączniki w postaci screenshotów i szczegółowy opis wykonywanych czynności w pliku '2023.05.14 NOTATKA z projektu nr 2, zadanie 1.docx

# Zadanie numer 2:

Do zadania 2 wykorzystane narzędzia:
1. hash-identifier
2. hashcat

Do zadania 2 - 1/2, 2/2 pkt.1-5, wykonaliśmy następujące czynności:
Wszystkie wykonane w Kalim.
1. W konsoli uruchomiliśmy program 'hash-dentifier' - poleceniem: hash-dentifier
2. W wyżej wymienionym programie wkleiliśmy hash.
3. W wyniku dostaliśmy informację jaki typ algorytmu został użyty.
4. W tym zadaniu trzeba było wykorzystać metodę słownikową z wykorzystanie 50 losowych haseł z pliku rockyou.txt
   - Najpierw stworzyliśmy plik o nazwie rockyou-50.txt 
     poleceniem 'shuf -n 50 /usr/share/wordlists/rockyou.txt > rockyou-50.txt'

Następnie w konsoli używając 'hashcat' podjęliśmy próbę złamania hasła metodą brute-force (plikiem rockyou-50.txt)
   Aby to zrobić było trzeba użyć następujących znaczników:
   - '-a 3'    - co oznacza atack mode 3 (brute force)
   - '-m 0'    - co oznacza algorytm 0 - co oznacza algorytm MD5
   - '-m 100'  - co oznacza algorytm 100 - co oznacza algorytm SHA-1
   - '-m 1700' - co oznacza algorytm 1700 - co oznacza algorytm SHA-512
   W Projekcie 2 zostały użyte tylkko w/w algorytmy.
   
Żeby nie robić dużej ilości screenshotów każdy wynik łamania hasła zapisywaliśmy do pliku .txt

koniec zadania nr 2.

# Zadanie numer 3:

Do zadania nr 3 wykorzystane narzędzia:
- wireshark
- przeglądarka firefox

Wykonaliśmy pkt.1-4 po kolei rezultaty są widoczne na screenshotach.
Do logowania użyliśmy (login: abra, hasło: kadabra)
Znaleźliśmy powyższe informację procesie nr 61(HTTP - GET).
Okazało się, że login i hasło jest w jednym procesie, w jednej linijce.

Nie da się wykonać tych samych czynności dla strony https://facebook.com ponieważ facebook używa SSL, a ten ruch jest nie widoczny w wiresharku.

Koniec zadania nr 3.

# Zadanie numer 4:

Do zadania nr 4 wykorzystaliśmy narzędzia:
- wireshark

Do zadania nr 4 wykorzystaliśmy 2 wirtualne maszyny:
- Kali Linux
- SDA (Ubuntu)

1. Po uruchomieniu nasłuchu w wireshark'u przeszliśmy do konsoli.
2. Sprawdziliśmy w maszynie SDA jaki jest IP '10.0.2.10'
3. Nawiązaliśmy połączenie pomiędzy Kalim a SDA po SSH 
   poleceniem 'ssh root@10.0.2.10' - 'hasło: 666'
4. Przeszliśmy do katalogu '/home/uranus'
   Utworzyliśmy pliki sekret1.txt i sekret2.txt z tajnymi hasłami poleceniami:
   - 'echo "Tekst do pliku sekret1" > sekret1.txt'
   - 'echo "Tekst do pliku sekret2" > sekret2.txt'
5. Dokonaliśmy edycję konfiguracji usługi vsFTPd poleceniem 'vim vsftpd.conf'
   - plik znajdował się w katalogu '/etc' 
   - zmieniliśmy opcję 'write_enable=NO' na 'write_enable=YES'
   - wykonaliśmy restart usługi vsFTPd poleceniem 'systemctl restart vsftpd'
   - sprawdziliśmy status usługi 'systemctl status vsftpd'

6. Zakończyliśmy nasłuch w wireshark'u
7. Przy nasłuchu ruchu SSH nie widać pakietów z plikami .txt

Koniec zadania nr 4.

# Zadanie numer 5:

Do zadania nr 5 wykorzystaliśmy narzędzia:
- wireshark

Do zadania nr 5 wykorzystaliśmy 2 wirtualne maszyny:
- Kali Linux
- SDA (Ubuntu)

1. Po uruchomieniu nasłuchu w wireshark'u przeszliśmy do konsoli.
2. Utworzyliśmy plik tekstowy 'echo "plik z wlasna zawartoscia do zadania nr 5" > plik_do_zadania_nr_5.txt'
3. Nawiązaliśmy połączenie pomiędzy Kalim a SDA po FTP 
   poleceniem 'ftp uranus@10.0.2.10' - 'hasło: butterfly'
4. Sprawdziliśmy adres IP Kaliego '10.0.2.5'
5. Ściągnęliśmy z maszyny SDA do Kaliego pliki sekret1.txt oraz sekret2.txt
   - 'get sekret1.txt'
   - 'get sekret2.txt'
6. Wysłaliśmy z Kaliego plik do maszyny SDA plik plik_do_zadania_nr_5.txt
   - 'put plik_do_zadania_nr_5.txt'
   - plik znajduje się w katalogu '/home/uranus'
7. Zakończyliśmy nasłuch w wireshark'u
8. Odszukaliśmy przesłany plik i ściagnięte pliki w wireshark'u wykorzystując w filtrze 'ftp-data'.

Koniec zadania nr 5.

