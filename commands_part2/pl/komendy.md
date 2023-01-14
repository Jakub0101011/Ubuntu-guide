# Komendy ubuntu część 2

## Dopisanie potoku na koniec pliku
echo "test test" >> plik

## Skasowanie całej zawartości pliku i dodanie potoku
echo "test test" > plik

---

**Użytkownicy**

---

/etc/passwd - lista wszystkich użytkowników z informacjami o nich

/etc/group - lista wszystkich grup w systemie

/etc/shadow - hasła użytkowników (zahashowane)

## Tworzenie nowych użytkowników
adduser

## Przełączanie się pomiędzy użytkownikami
su

## Sprawdzanie obecnego użytkownika
whoami

## Wylogowanie
exit

> ^ = Ctrl

> ^+d - to samo jak exit tylko że skrótem (małe d)

## Usuwanie użytkownika
deluser
- --remove-home (usunie jego homedir)

## Dodawanie nowej grupy systemowej
addgroup

## Usuwanie grupy systemowej
delgroup

## Wyświetlanie grup użytkownika
- groups

- groups nazwa_użytkownika (wyświetlenie grup innego użytkownika)

- cat /etc/group | grep user

## Przypisanie użytkownika do grupy
usermod -aG grupa user

> operacje na grupach wymagają przelogowania

## Skasowanie użytkownika z grupy (podanie grup bez tej z której usuwamy)
usermod -G grupa1,grupa2 user

## Zablokowanie konta użytkownika
usermod -L user
> zablokowane konto uniemożliwia np dostęp przez SSH (nie zalogujemy się przez SSH do systemu z wykorzystaniem tego konta)

## Odblokowanie konta użytkownika
usermod -U user

## Zmiana hasła użytkownika
passwd
> jako argument można podać nazwę użytkownika

## Modyfikacja haseł
chage
- -l user (wyświetli informacje o haśle użytkownika)

- -d 0 (wymusi zmianę hasła)

- -M x (jak długo ma być ważne hasło)

---

**Konto administratora = roota**

---

## Wykonanie zadania jako zwykły użytkownik, ale z uprawnieniami roota
sudo

## Przełącza na konto roota
sudo su

## Dodanie użytkownika do grupy sudo
cat /etc/group | grep wheel lub sudo

usermod -aG sudo user

sudo apt update

## Powrót do części 1
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part1/pl/komendy.md)

## Przejdź dalej do części 3
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part3/pl/komendy.md)