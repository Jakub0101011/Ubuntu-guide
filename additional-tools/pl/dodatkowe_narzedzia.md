# Dodatkowe narzędzia dla Linuxa

## Znajdź i zabij dany proces
pgrep -fl **nazwa_procesu**
pkill -f **nazwa_procesu**

## Htop
F5 - ten skrót pokazuje drzewo procesów, wtedy wystarczy tylko ubić proces nadrzędny

## MTR (rozbudowany ping)
pokazuje nam ping + traceroute

> czyli puszcza ping po wszystkich hopkach po drodze i sprawdza co się dzieje w trakcie komunikacji

## SOCAT (komunikator terminalowy)
uruchamiamy serwer: 
        
    socat TCP4-LISTEN:81 STDOUT

> port dowolny

podłączamy się klientem:

    socat - TCP4:1.1.1.1:81

> podajemy IP i Port serwera

## iptraf/iftop (statystyki połączenia sieciowego)

## | pipe (przekazuje standardowe wyjście)

3>&1 1>&2 2>&3 3>&-

> 1 - stdout

> 2 - stderr

> (-) zamknięcie deskryptora

> & = deskryptor, czyli na coś pokazuje (np. terminal)

> ^ - zamiana kolejnością stdout i stderror

weź to na co pokazuje 1 (czyli stdout) i zrób tak, żeby trójka (czyli nic) pokazywała na to samo
weź dwójkę (czyli stderr) i zrób tak, żeby jedynka (czyli stdout) pokazywała na to, na co pokazuje dwóka 
weź to na co pokazuje trójka (czyli nasze stare stdout) i zrób, aby pokazywała na to na co wskazuje dwójka czyli stderr
na końcu zrób porządek i zamknij deskryptor trzeci

echo "test" 1>/dev/null = wyślij standardowe wyjście (stdout) do nulla

## Uruchomienie komendy po restartcie systemu w cronie
zamiast * podajemy @reboot i komenda