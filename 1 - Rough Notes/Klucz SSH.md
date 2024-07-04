
--- 
tags: [[Git]] [[Visual Studio]]
date: 2024-07-04

---
# Klucz SSH
Umożliwia identyfikację, za pomocą której możemy połączyć repozytorium znajdujące się lokalnie na urządzeniu z tym zdalnym na Githubie.

Do połączenia lokalnego urządzenia z kontem na Githubie służy klucz SSH. Aby wygenerować klucz lokalnie do git bash wpisujemy: `ssh-keygen -t rsa -b 4096 -C “emial@github”` 

Są dwa klucze:
==**Klucz publiczny**== to ten, który chcemy opublikować na naszym githubie.
==**Klucz prywatny**== powinien być zachowany na naszym urządzeniu i nikt oprócz nas nie powinien mieć do niego dostępu.

Za każdym razem, kiedy chcemy podłączyć githuba, spushować kod na githuba lub użyć konta za pośrednictwem lokalnego urządzenia. Klucze to matematyczny dowód, że ja za pośrednictwem klucza prywatnego wygenerowałam klucz publiczny.

## 3 najważniejsze kroki:
1. Generowanie klucza SSH na urządzeniu lokalnym
2. Dodawania klucza SSH do ssh-agenta
3. Dodawanie klucza SSH na githuba


### KROK 1:  Generowanie klucza SSH na urządzeniu lokalnym


1. Otwórz Git Bash.

2. Wklej poniższy tekst ze swoim githubowym adresem mailem 
	`ssh-keygen -t ed25519 -C "your_email@example.com"`
	Uwaga: jeśli używasz starszego systemu, który nie obsługuje algorytmu Ed25519, użyj:
	`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	To tworzy nowy klucz SSH.

Gdy zostanie wyświetlony komunikat „Wprowadź plik, w którym chcesz zapisać klucz”, naciśnij Enter, aby zaakceptować domyślną lokalizację pliku. Pamiętaj, że jeśli wcześniej utworzyłeś klucze SSH, ssh-keygen może poprosić cię o przepisanie innego klucza. W takim przypadku zalecamy utworzenie klucza SSH o niestandardowej nazwie. Aby to zrobić, wpisz domyślną lokalizację pliku i zastąp id_ALGORITHM niestandardową nazwą klucza.
>` Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]`

W zapytaniu wpisz bezpieczne hasło. 
>` Enter passphrase (empty for no passphrase): [Type a passphrase]`
>` Enter same passphrase again: [Type passphrase again]`


### KROK 2:  Dodawania klucza SSH do ssh-agenta

Przed dodaniem nowego klucza SSH do agenta ssh w celu zarządzania kluczami, powinieneś sprawdzić istniejące klucze SSH i wygenerować nowy klucz SSH. 

1. W terminalu GitBash upewnij się, że agent ssh jest uruchomiony z poziomu admina. (zakładka Linux):
`$ eval "$(ssh-agent -s)"
` Agent pid 59566`

2. W oknie terminala bez podwyższonych uprawnień dodaj swój klucz prywatny SSH do agenta ssh. Jeśli utworzyłeś klucz o innej nazwie lub dodajesz istniejący klucz o innej nazwie, zastąp id_ed25519 w poleceniu nazwą pliku klucza prywatnego.
`ssh-add c:/Users/adaku/.ssh/id_ed25519`

### KROK 3:  Dodawanie klucza SSH na githuba
Zakładka w ustawieniach:
**![](https://lh7-us.googleusercontent.com/docsz/AD_4nXdRwK3412Ri9aLMumTXj2hdnf_GgGSVCH-8NkBnDBjsUcTTTilvfQ2zfYa-1y5uJBogC4D5O0M07XHXfcmQpo1WnrjUVWR5rvZP_C7MXYLxFj8FCjCRvGYy9YVE2zRvu5LeyCuq-EdSTtlpUxNPyaHd3Ss?key=D1idJOhe54BrrVYEtZdo4g)**

**![](https://lh7-us.googleusercontent.com/docsz/AD_4nXcDgdJxfJ1X3rECkSl7WNn3wFiRLAGRuP4fUxRph3Sv6bJAL037BBPgB3Sx5RYNcJFQxzNCQ0w4iNomSqatRbC-LSpu8X_G1OzGYAZOiFmGx4OKdPlFIkWpL65mMbQnGrIKWW4YZ4-b76iyl17DtK5Chid0?key=D1idJOhe54BrrVYEtZdo4g)**

**![](https://lh7-us.googleusercontent.com/docsz/AD_4nXfHAwrCX-FakXzGUWRGBcNBejRPwAvsuqvmIR4s3ZYpu-ZlzzyC7xxXbGScE0U19q6UjV7AFNR4BPc7UejJ39aMwDdT3czBdY0p8vnqZjIuomZ8SlfAw9vqOg2JLeLO7lK9rCmyjmdWFB8XJopK4CuBWQ4?key=D1idJOhe54BrrVYEtZdo4g)**
### References:
https://www.youtube.com/watch?v=RGOj5yH7evk&t=1069s

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent 
---



