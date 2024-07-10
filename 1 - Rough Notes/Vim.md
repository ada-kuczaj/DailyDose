
--- 
tags: [[Linux]] [[Visual Studio]] 
date: 2024-07-08

---

Vim to zaawansowany edytor tekstu. Vim działa głównie w trybie tekstowym, co czyni go bardzo lekkim i szybkim narzędziem.

Podstawowe skróty klawiszowe do poruszania się w Vimie w 

### Trybie normalnym:

- `h`: przesunięcie kursora w lewo
- `j`: przesunięcie kursora w dół
- `k`: przesunięcie kursora w górę
- `l`: przesunięcie kursora w prawo

Oprócz podstawowych skrótów poruszania się, istnieje wiele innych przydatnych poleceń i skrótów w Vimie:

### Tryby pracy:

- `i`: wejście w tryb wstawiania (insert mode)
- `Esc`: wyjście z trybu wstawiania do trybu normalnego
- `v`: wejście w tryb wizualny (visual mode) do zaznaczania tekstu
- `:`: wejście w tryb poleceń (command mode)

### Operacje edycyjne:

- `x`: usunięcie znaku pod kursorem
- `dd`: usunięcie bieżącej linii
- `yy`: skopiowanie bieżącej linii
- `p`: wklejenie po bieżącej pozycji kursora
- `u`: cofnięcie ostatniej operacji
- `Ctrl+r`: powtórzenie cofniętej operacji

### Poruszanie się po pliku:

- `gg`: przejście na początek pliku
- `G`: przejście na koniec pliku
- `0`: przejście na początek linii
- `$`: przejście na koniec linii
- `w`: przejście do początku następnego słowa
- `b`: przejście do początku poprzedniego słowa

- **Kopiowanie (Yank)**:
	- Aby skopiować (yank) jedną linię, umieść kursor na linii i naciśnij `yy`.
    - Aby skopiować wiele linii, na przykład 5 linii, naciśnij `5yy`.
    - Aby skopiować tekst od kursora do końca linii, naciśnij `y$`.
    - Aby skopiować cały plik, użyj polecenia `ggVGy`.
- 
- **Wklejanie (Put)**:    
    - Aby wkleić (put) skopiowany tekst poniżej kursora, naciśnij `p`.
    - Aby wkleić skopiowany tekst powyżej kursora, naciśnij `P`.
- 
- **Wycinanie (Delete)**:    
    - Aby wyciąć jedną linię, umieść kursor na linii i naciśnij `dd`.
    - Aby wyciąć wiele linii, na przykład 3 linie, naciśnij `3dd`.
    - Aby wyciąć tekst od kursora do końca linii, naciśnij `d$`.
- 
- **Operacje na zaznaczonym tekście**:
	- Aby zaznaczyć tekst, przejdź do trybu wizualnego, naciskając `v` dla trybu wizualnego, `V` dla trybu wizualnego liniowego, lub `Ctrl + v` dla trybu wizualnego blokowego.
    - Po zaznaczeniu tekstu, naciśnij `y` aby skopiować lub `d` aby wyciąć.
    - Następnie naciśnij `p` lub `P`, aby wkleić tekst w odpowiednim miejscu.
- 
- **Korzystanie z systemowego schowka**:
    - Aby korzystać ze schowka systemowego, użyj znaków `"` oraz `+` przed poleceniami yank, put, lub delete.
    - Na przykład, aby skopiować do schowka systemowego, zaznacz tekst w trybie wizualnym (`v`) i naciśnij `"+y`.
    - Aby wkleić ze schowka systemowego, naciśnij `"+p`.

### References:


---



