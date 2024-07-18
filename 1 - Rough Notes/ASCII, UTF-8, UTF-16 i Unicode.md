
--- 
tags: [[JS]]
date: 2024-07-16

---
#### ASCII

ASCII (American Standard Code for Information Interchange) to pierwotny standard kodowania znaków używany w komputerach. ASCII używa 7-bitowego kodowania, co daje 128 możliwych znaków, obejmujących:

- Litery alfabetu łacińskiego (zarówno małe, jak i wielkie litery)
- Cyfry
- Znaki specjalne (np. interpunkcyjne)
- Kontrolne kody (np. znaki nowej linii)

#### UTF-8

UTF-8 (8-bit Unicode Transformation Format) to standard kodowania znaków Unicode, który jest kompatybilny z ASCII. Jest to zmienno-długościowe kodowanie, co oznacza, że jeden znak może być reprezentowany przez 1 do 4 bajtów:

- Znaki ASCII (0-127) są kodowane jako pojedynczy bajt
- Znaki spoza ASCII są kodowane jako 2, 3 lub 4 bajty, w zależności od ich wartości.

UTF-8 jest obecnie najczęściej używanym kodowaniem znaków w Internecie ze względu na swoją efektywność i kompatybilność wsteczną z ASCII.

#### UTF-16

UTF-16 (16-bit Unicode Transformation Format) to inny sposób kodowania znaków Unicode, który używa 16-bitowych jednostek kodowych. Jest to również zmienno-długościowe kodowanie:

- Znaki z podstawowego bloku Unicode (U+0000 do U+FFFF) są kodowane jako pojedyncza 16-bitowa jednostka.
- Znaki spoza tego bloku (tzw. "surrogate pairs") są kodowane jako dwie 16-bitowe jednostki (łącznie 4 bajty).

UTF-16 jest często używany wewnętrznie przez systemy operacyjne i aplikacje, takie jak Windows i Java.



Zarówno UTF-8, jak i UTF-16 są kodowaniami Unicode, co oznacza, że ​​mogą reprezentować ogromny zakres znaków, w tym:

- Tekst w większości języków i pism świata
- Tekst historyczny
- Emoji

#### Punkty kodowe a jednostki kodowe Unicode

- **Punkt kodowy Unicode (Unicode code point)**: Jest to unikalny numer przypisany do każdego znaku w standardzie Unicode. Punkty kodowe są zazwyczaj zapisywane w formacie "U+XXXX", gdzie "XXXX" jest 16-bitową liczbą szesnastkową.
- **Jednostka kodowa (Code unit)**: Jest to jednostka pamięci używana do reprezentacji punktu kodowego w konkretnym kodowaniu (np. UTF-8, UTF-16). W UTF-8 jednostką kodową jest bajt (8-bit), natomiast w UTF-16 jest to 16-bitowa jednostka.

W skrócie, punkty kodowe są abstrakcyjnymi reprezentacjami znaków, natomiast jednostki kodowe są konkretnymi bitowymi reprezentacjami tych znaków w różnych systemach kodowania.



### References:


---



