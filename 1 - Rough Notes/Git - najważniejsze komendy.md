
--- 
tags: [[Git]]
date: 2024-07-04

---

### Git - system kontroli wersji, służy do śledzenia zmian w kodzie

cd - change directory; podwójne kliknięcie na folder
cd .. - cofasz się do wcześniejszego/wyższego folderu
rm nazwaPliku -  usunie plik z katalogu  
rm -rf nazwaPliku - wymuszenie usunięcia katalogu wraz z wszystkimi jego zawartościami 
git remote - wyświetla listę zdalnych repozytoriów skonfigurowanych dla lokalnego repo 
git clone adresSSHzGita - przenieś repozytorium z Githuba do lokalnego folderu
git add . / git add nazwaPliku - przenieś zmodyfikowane pliki do staging area
git commit -m “what and why” -m “description” - zapisz pliki w Git + treść wiadomości
git push - wypchnij zmiany na zdalne repozytorium na Githubie
git pull - ściągnij zmiany ze zdalnego repozytorium na lokalny folder
ls -la - wypisz listę wszystkich plików w folderze (również tych ukrytych)
git status - pokazuje stan wszystkich plików
git-ls-files - pokaż informacje o plikach w indeksie i drzewie roboczym
git-cat-file - podaje zawartość lub szczegóły obiektów w repozytorium

dodawanie nowej gałęzi:
git branch - pokaż listę gałęzi
git checkout -b nazwaGałęzi - tworzy nową  gałąź
git checkout nazwaGałęzi - przechodzi do gałęzi której nazwę wpisałeś
git push origin nazwa Gałęzi - przesłanie zmian z lokalnego brancha do zdalnego repozytorium
git branch -D nazwaGałęzi - usuwa  gałąź (nie możesz na niej być)
git log - pełna historia zmian
git log -1 - pokazuje ostatnią zmianę
git stash  - jest używane do tymczasowego zapisania zmian w katalogu roboczym, aby można było wrócić do czystego stanu roboczego bez tworzenia commitu


git diff filename - porównuje unstaged plik z ostatnią zacommitowaną wersją
git diff -r HEAD filename - porównuje staged file z ostatnią zacommitowaną wersją
git diff -r HEAD- porównuje wszystkie pliki w staging area z poprzednią zacommittowaną wersją

git show HEAD~1 - pokazuje co się zmieniło w przedostatnim commicie
git diff 35f4b4d 186398f - pokazuje różnice pomiędzy dwoma commitami
git diff HEAD~1 HEAD~2 - pokazuje różnice pomiędzy dwoma commitami
git annotate file - pokazuje linijka po linijce zmiany i powiązane dane

3 sposoby na unstaging pojedynczy plik:
git reset HEAD nazwapliku
nano nazwapliku
git add nazwapliku

git checkout . -cofnij zmiany we wszystkich unstaged plikach w repozytorium
git clean -n -pokazuje które pliki nie są śledzone
git clean -f - usuwa nieśledzone pliki (nie można cofnąć)
git diff main nazwabrancha - pokazuje różnicę pomiędzy branchami
### References:

https://www.atlassian.com/git/glossary#commands
---



