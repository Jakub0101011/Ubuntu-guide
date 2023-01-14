# Komendy ubuntu część 3

## Wylistowanie uprawnień do plików / katalogów
ls -l

## Opis uprawnień
- rwx r-x r-x

plik/katalog - uprawnienia dla właściciela (u) 

uprawnienia dla grupy (g) 

uprawnienia dla pozostałych (o)

właściciel(u-ser) grupa(g-roup) pozostali(o-ther) + -

wszyscy (a-ll)

| prawo dostępu        | wartość cyfrowa           | wartość liczbowa |
|-------------|:-------------:|:-------------:|
| odczyt      | r | 4 |
|zapis| w | 2 |
|wykonanie| x | 1 |

## Zmiana właściciela
chown
- user

- :grupa

- user:grupa

## Zmiana uprawnień
chmod
- 000 plik

- 777 plik

- o+wx,g+r

- ugo+w

- g-r

---

**System**

---

## Sprawdzenie jak długo pracuje system
uptime

## Sprawdzenie zajętości dysków lokalnych 
df
- -h

## Sprawdzenie zajętości dysku
du
- -sh (sumaryczne dla danego katalogu)

## Sprawdzenie wykorzystania pamięci RAM
free
- -h

---

**Zarządzanie oprogramowaniem**

---

Linux posiada własne repozytoria oprogramowania, z których w łatwy sposób możemy instalować oprogramowanie w systemie,

Repozytoria są to specjalne serwery, na których składowane są wszystkie pakiety (programy, pakiety, instalki).


## Narzędzie apt
apt
- update - zaktualizuje repozytorium (sprawdzi jakie są najnowsze wersje pakietów)

- upgrade - zaktualizuje pakiety zainstalowane w systemie; 

> zalecane najpierw wykonanie update 

> ! Komendy występujące po sobie rozdzielamy średnikiem: apt update; apt upgrade

- search - wyszuka pakiet w repozytorium

- install - instaluje (htop, mc)

- remove - odinstaluje

- list --installed - wylistuje pakiety zainstalowane w systemie
	
## Instalacja pakietu htop

[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/tree/main/installation-htop)

## Powrót do części 2
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part2/pl/komendy.md)

## Przejdź dalej do części 4
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part4/pl/komendy.md)