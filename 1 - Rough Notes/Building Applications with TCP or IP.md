
--- 
tags: [[Internet]]
date: 2024-07-15

---
### TCP/IP (Transmission Control Protocol/Internet Protocol)

To podstawowy protokół komunikacyjny, który zapewnia niezawodne, uporządkowane i sprawdzone pod względem błędów dostarczanie danych pomiędzy aplikacjami działającymi na różnych urządzeniach.

### Tworząc aplikacje za pomocą protokołu TCP/IP, należy zrozumieć kilka kluczowych pojęć:

1. **Porty** -służą do identyfikacji aplikacji lub usługi działającej na urządzeniu. Każdej aplikacji lub usłudze przypisany jest unikalny numer portu, umożliwiający przesłanie danych do właściwego miejsca docelowego.
2. **Gniazda** (Sockets) - to kombinacja adresu IP i numeru portu reprezentującego konkretny punkt końcowy komunikacji. Gniazda służą do nawiązywania połączeń pomiędzy urządzeniami i przesyłania danych pomiędzy aplikacjami.
3. **Połączenia** - połączenie między dwoma gniazdami jest ustanawiane, gdy dwa urządzenia chcą się ze sobą komunikować. Podczas procesu nawiązywania połączenia urządzenia negocjują różne parametry, takie jak maksymalny rozmiar segmentu i rozmiar okna, które określają sposób przesyłania danych przez połączenie.
4. **Przesyłanie danych** -po nawiązaniu połączenia dane można przesyłać pomiędzy aplikacjami uruchomionymi na każdym urządzeniu. Dane są zazwyczaj przesyłane w segmentach, przy czym każdy segment zawiera numer kolejny i inne metadane zapewniające niezawodne dostarczanie.


### References:
https://cs.fyi/guide/how-does-internet-work

---



