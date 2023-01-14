# Komendy ubuntu część 4


**Sieci**

---

## Sprawdzenie konfiguracji IP kart sieciowych
ip a 

## Wyświetlenie tras routingu
ip route
	
## Obsługa stanu kart sieciowych 
ip l set enp1s0 down/up 

> (l-link czyli połączenie, karta)

> jeżeli wyłączymy nie będzie widocznych ustawień IP, a w statusie obok nazwy NIC (Network Interface Card) będzie DOWN


---

**Konfiguracja ustawień IP - NETPLAN**

---

- zapisane jako YAML (YAML to język IT przeznaczony do prezentowania danych w ustrukturalizowany sposób; język opisowy)

- język wrażliwy na składnie 
> (wcięć nie robimy tabami tylko spacjami)

- pliki konfiguracyjne znajdziemy w lokalizacji /etc/netplan/*.yaml

- w jednym pliku możemy mieć konfigurację kilku NIC

0. Do VM dodajemy drugą kartę sieciową. Obie ustawiamy jako bridged na swój obecnie używany interfejs sieciowy w laptopie.

1. Sprawdzamy jakie pliki mamy w katalogu /etc/netplan. Domyślnie jest tylko jeden - to właśnie w nim będziemy konfigurować ustawienia IP kart sieciowych.

2. Interesuje nas poniższy fragment :   

konfiguracja kart sieciowych
ethernets: 

nazwa interfejsu sieciowego (do sprawdzenia np poprzez ip a)
       
DEVICE_NAME:

czy adres IPv4 będzie pobierany z serwera dhcp?
          
Dhcp4: true/false

adress IP dla karty sieciowej / maska sieciowa
          
Addresses: [IP_ADDRESS/NETMASK]

adress IP routera
          
Gateway4: GATEWAY

sekcja konfiguracji serwerów DNS
          
Nameservers:

ustawienie adresów IP serwerów DNS  
             Addresses: [NAMESERVER_1, NAMESERVER_2]
             
**Ćwiczenie - dla pierwszej karty sieciowej ustawiamy, aby pobierała adres IP z serwera DHCP, dla drugiej przypisujemy adres 192.168.1.200/24 (netplan.png)**

	ethernets:

     enp0s3:

        dhcp4: true

     enp0s8:

        dhcp4: false

        addresses: [192.168.1.200/24]

        gateway4: 192.168.1.1

        nameservers:

           addresses: [8.8.8.8,1.1.1.1]

3. Sprawdzenie konfiguracji netplan:

netplan try

4. Jeżeli powyższe nie zwróciło błędów zastosowanie ustawień:

netplan apply

## Zmiana hostname (hostname - nazwa sieciowa hosta)
hostname (wyświetlenie obecnej nazwy)

zmiana następuje w dwóch miejscach:

/etc/hostname

/etc/hosts

> trzeba podmienić starą nazwę na nową


## Diagnozowanie komunikacji sieciowej
ping

1.1.1.1 (po adresie IP)

facebook.com (po nazwie domenowej - tutaj dodatkowa opcja sprawdzenia serwera DNS, który najpierw przetłumaczy nazwę domenową na adres IP, następnie wykona ping)
	
> w przypadku braku komendy ping należy zainstalować pakiet iputils-ping

---

**Zarządzanie usługami**

---

## Zarządzanie usługami systemowymi odbywa się z wykorzystaniem narzędzia systemctl
systemctl 

enable (uruchamianie przy starcie systemu)

disable (nie uruchamianie przy starcie systemu)

start (uruchom usługę teraz)

stop (zatrzymaj usługe teraz)

restart (uruchom ponownie usługe)

status (sprawdź status usługi)

reload (załaduj ponownie pliki konfiguracyjne, bez restartu usługi)
	
> systemctl enable --now nazwa_usługi <- sprawi, aby uruchamiała się przy starcie, ale również aby nastąpił start usługi w tym momencie; enable+start
	
> na przykładzie usługi SSH

> systemctl status ssh

> systemctl restart ssh

---

**Serwer SSH**

---

## Logowanie lokalne
Bezpośrednio do wirtualnej maszyny, bądź fizycznego komputera.

## Logowanie zdalne - SSH
SSH (Secure Shell) - protokół do zdalnego zarządzania hostami. Następca protokołu telnet. Wyróżnia się tym, że cały ruch na linii klient-serwer jest szyfrowany.
Domyślnie działa na porcie 22/TCP.

## Instalacja oprogramowania
pakiet dla serwera: openssh-server

pakiet dla klienta: openssh-client

## Podłączanie do serwera
z poziomu systemu Windows:
	
program Putty, podajemy adres IP, port, login i hasło

z poziomu systemu Linux:

ssh login@host (ip, bądź nazwa domenowa)

ssh -p 1234 technik@1.1.1.1
	
> Przed wprowadzeniem zmian sprawdźmy jak działa serwer na domyślnych ustawieniach.

> Spróbujmy zablokować użytkownika (usermod -L user), a następnie zalogujmy się na niego przez SSH.
	
> 1. Logujemy się na usera, logout.
	
> 2. Blokujemy.
	
> 3. Próbujemy zalogować się na niego.
	
> 4. Odblokowujemy.
	
> 5. Ponownie próbujemy się zalogować.

## Zmiana konfiguracji serwera
Aby zmiany wprowadzone w plikach konfiguracyjnych weszły w życie należy uruchomić ponownie daną usługę

Plik konfiguracyjny serwera SSH:

/etc/ssh/sshd_config 

**przed zmianami zawsze wykonać backup plików konfiguracyjnych, np cp /etc/ssh/sshd_config /etc/ssh/sshd_config_bckp**

Zmiana domyślnego portu:

Port 22 

Domyślny wpis. 

Hashtag na początku linii oznacza komentarz (dana linia nie brana jest pod uwagę).

Usuwamy komentarz i zmieniamy port na dowolny, powyżej 1024. Ustawmy 1234:

Port 1234
	
Wyłączenie możliwości logowania roota:

#PermitRootLogin prohibit-password

Włączamy opcję, więc kasujemy komentarz. Zmieniamy argument na no:

PermitRootLogin no
	
Przydzielenie dostępu użytkownikom: (dodać na końcu)

DenyUsers nazwa_użytkownika (wszyscy inni mają dostęp z wyjątkiem użytkowników podanych tutaj)

AllowUsers user1 , user2 (jeżeli dam Allow to dopuszcza tylko tych użytkowników podanych w tej deklaracji)

**spacja przecinek spacja**
			
Wyłączenie wyświetlania baneru

#Banner none

Włączamy opcję, więc kasujemy komentarz.

Banner jest to informacja jaka się wyświetla po zalogowaniu do ssh. Zawiera m. in. wersje systemu czy kernela. Gdy osoba niepowołana uzyska takie informacje ułatwi jej to włamanie / przejęcie serwera.

## Logowanie bez hasła
Do tej pory używaliśmy logowania z wykorzystaniem nazwy użytkownika i hasła.
Jest możliwość logowania za pomocą klucza SSH (dużo bezpieczniejsze, ponieważ hasło może zostać złamane / wykradzione).

> ćwiczenie wykonujemy na systemach Linux

Na kliencie generujemy klucz ssh:

ssh-keygen -t rsa -b 4096 
	
Kopiujemy wygenerowany klucz na serwer:

ssh-copy-id nazwa_uzytkownika_na_serwerze@ip_serwera

podajemy hasło użytkownika na serwerze
	
Jeżeli chcemy logować się na różnych użytkowników, dla każdego musimy oddzielnie kopiować klucz ssh.
	
W przypadku, gdy serwer nasłuchuje na porcie innym niż domyślny musimy podać w komendzie port:

ssh-copy-id -p port_nr user@host
	
W pliku konfiguracyjnym serwera SSH wyłączamy opcje logowania z wykorzystaniem hasła:
	
#PasswordAuthentication yes
	
PasswordAuthentication no
	
> Jeżeli chcemy, aby część użytkowników logowała się przez klucz ssh, a część po haśle musimy zostawić powyższą deklarację z argumentem yes.

---

**BONUS - komunikator terminalowy**

---

Wykorzystamy do tego narzędzie o nazwie socat

## Uruchamiamy serwer:
socat TCP4-LISTEN:81 STDOUT

> (port dowolny)

## Podłączamy się klientem:
socat - TCP4:1.1.1.1:81

> podajemy IP i PORT serwera

> w tym momencie możemy wysyłać wiadomości pomiędzy dwoma hostami