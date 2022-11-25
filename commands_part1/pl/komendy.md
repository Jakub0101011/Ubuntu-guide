# Komendy ubuntu część 1

## Link do struktur katalogów:
(struktury)[https://ubuntu.com.pl/linux-struktura-katalogow/]

## Pomoc
man

--help

## Poruszanie się po drzewie katalogów

cd - zmiana katalogu
- /

- /var/log

- . (czyli katalog w którym się znajdujesz)

- .. (katalog wyżej)

- ~ (wracanie do home'a)

pwd - wyświetla aktualny katalog

## Listowanie zawartości katalogów

ls
- l (w formie listy)

- la (pokazuje pliki ukryte - zaczynające się od **.**)

- lA (pokazuje pliki ukryte, ale ukrywa biężący katalog **.** i katalog wyżej **..**)

- lR (pokazuje listę rekursywnie - wyświetla zawartość katalogów wewnątrz)

## Wyświetlanie i przeszukiwanie zawartości plików
cat - wyświetla zawartość pliki

grep (wyraz) (plik) - wyszukuje wyraz w podanym pliki
- -i (nie zwraca uwagi na wielkość liter)

cat plik | grep wyraz - wyszukuje wyraz w potoku, w którym znajduje się zawartość pliki

grep "fraza*" "*/*" - wyszukuje frazę zaczynającą się na "fraza" we wszystkich plikach w tym katalogu (wewnątrz katalogów)

head - wyświetla pierwsze linie pliku
- -n (podaną ilość wierszy)

tail - wyświetla ostatnie linie pliku

- -n (podaną ilość wierszy)

- -f (odświeża na bieżąco, jeżeli coś wskoczy do pliku wyświetli)

> Przydatne podczas śledzenia logów

more - interaktywne przeglądanie pliku

## Tworzenie katalogów
mkdir
- -p (całe drzewo)

- kilka katalogów rozdzielamy spacją

## Tworzenie lub edytowanie plików
nano - edytor tekstowy

touch

## Kopiowanie oraz przenoszenie plików i katalogów
cp (źródło) (cel) - kopiowanie plików lub katalogów

- -r (rekursywnie, cały katalog)

mv (źródło albo stara nazwa pliku) (cel albo nowa nazwa pliku) - przenoszenie plików lub katalogów oraz zmiana nazwy pliku lub katalogów
- -r (rekursywnie, cały katalog)

## Usuwanie plików i katalogów
rm
- -r (wykorzystywane przy katalogach)

rm -r katalog/* (skasuje całą zawartość katalogu)

## Wyszukiwanie plików
find (gdzie) -name (nazwa pliku)

> np. find /home/ubuntu --name plik_1

## Host

Wyłączenie:

- shutdown -h now

Restart:

- reboot

Czas działania:

- uptime

##

^ = Ctrl

^+l - wyczyści ekran / terminal (małe L)

Tab - autodopełnianie

Parametry jedno literowe oznaczamy jednym -,
parametry dłuższe oznaczamy --

> np. -r, --name