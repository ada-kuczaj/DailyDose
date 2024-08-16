
--- 
tags: 
date: 2024-08-16

---
### <span style="color: #d11141;">Co to jest Docker?</span>

**Docker** to platforma open-source do automatyzacji wdrażania aplikacji jako lekkich, przenośnych, samodzielnych kontenerów. Kontenery te zawierają wszystko, co potrzebne do uruchomienia aplikacji – kod, środowisko uruchomieniowe, biblioteki i zależności. Dzięki temu aplikacje mogą być uruchamiane w dowolnym środowisku bez konieczności modyfikacji.

### <span style="color: #00b159;">Do czego służy Docker?</span>

Docker jest używany do:
- **Konsolidacji środowisk** – umożliwia uruchamianie aplikacji w tym samym środowisku na różnych maszynach, co eliminuje problemy związane z różnicami w konfiguracjach.
- **Izolacji aplikacji** – każda aplikacja działa w swoim własnym kontenerze, co zapewnia izolację i zwiększa bezpieczeństwo.
- **Szybkiego wdrażania** – Docker umożliwia szybkie tworzenie, testowanie i wdrażanie aplikacji.
- **Skalowania aplikacji** – kontenery mogą być łatwo kopiowane i skalowane w różnych środowiskach, co pozwala na lepsze zarządzanie zasobami.

### <span style="color: #00aedb;">Jak używać Dockera?</span>

Docker działa na zasadzie tworzenia i zarządzania kontenerami, które są uruchamiane na bazie obrazów (images). Obrazy są szablonami, które zawierają wszystkie zależności potrzebne do uruchomienia aplikacji.

Podstawowe komendy Docker to:
- **docker run** – uruchamia nowy kontener na podstawie podanego obrazu.
- **docker build** – tworzy nowy obraz na podstawie Dockerfile.
- **docker pull** – pobiera obraz z Docker Hub.
- **docker push** – wysyła obraz do Docker Hub.
- **docker ps** – wyświetla listę uruchomionych kontenerów.
- **docker stop** – zatrzymuje działający kontener.

### <span style="color: #f37735">Wirtualizacja - Co to jest i do czego służy?</span>

**Wirtualizacja** to technologia, która pozwala na tworzenie wirtualnych wersji zasobów komputerowych, takich jak systemy operacyjne, serwery, pamięć masowa, czy sieci. Wirtualizacja umożliwia uruchamianie wielu wirtualnych maszyn (VM) na jednym fizycznym urządzeniu, gdzie każda maszyna działa jak niezależny komputer z własnym systemem operacyjnym i aplikacjami.

#### Do czego służy wirtualizacja?

Wirtualizacja jest używana do:
1. **Konsolidacji zasobów**: Pozwala na uruchamianie wielu maszyn wirtualnych na jednym fizycznym serwerze, co zmniejsza zapotrzebowanie na sprzęt i redukuje koszty.
2. **Izolacji środowisk**: Każda maszyna wirtualna działa niezależnie, co pozwala na uruchamianie różnych systemów operacyjnych i aplikacji na tym samym fizycznym sprzęcie bez ryzyka konfliktów.
3. **Łatwego zarządzania i migracji**: Wirtualne maszyny mogą być łatwo przenoszone między różnymi serwerami bez konieczności przerywania pracy aplikacji.
4. **Testowania i rozwoju**: Programiści mogą tworzyć i testować aplikacje w odizolowanych środowiskach, które mogą być szybko tworzone i usuwane bez wpływu na inne procesy.
5. **Poprawy dostępności i odzyskiwania po awarii**: Wirtualizacja ułatwia tworzenie kopii zapasowych oraz szybkie przywracanie systemów w przypadku awarii sprzętu.

### References:
https://www.youtube.com/watch?v=pg19Z8LL06w
https://www.youtube.com/watch?v=ZyBBv1JmnWQ 
https://docs.docker.com/engine/install/ 
https://www.docker.com/products/docker-desktop/ 
https://www.youtube.com/watch?v=FG2Ak2rQcsI 
---



