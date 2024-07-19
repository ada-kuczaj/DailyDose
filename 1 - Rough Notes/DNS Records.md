
--- 
tags: [[DNS - podstawowe informacje]]
date: 2024-07-19

---

Film wyjaśnia różne typy rekordów DNS, które są kluczowe dla tłumaczenia nazw domen na adresy IP i inne funkcje DNS. Oto główne typy omówione w filmie:

1. **A Record**: Mapuje domenę na adres IPv4.
	- Przykład: `www.przyklad.com -> 192.168.1.1`
2. **AAAA Record**: Mapuje domenę na adres IPv6.
	- Przykład: `www.przyklad.com -> 2001:0db8:85a3:0000:0000:8a2e:0370:7334`
3. **CNAME Record**: Alias jednej domeny do innej.
	- Przykład: `blog.przyklad.com -> www.przyklad.com`
4. **MX Record**: Kieruje e-maile do serwera pocztowego.
	- Przykład: `przyklad.com -> mail.przyklad.com`
5. **TXT Record**: Przechowuje informacje tekstowe do różnych celów, np. SPF.
	- Przykład: `przyklad.com -> "v=spf1 include:_spf.google.com ~all"`
6. **NS Record**: Wskazuje autorytatywne serwery DNS dla domeny.
	- Przykład: `przyklad.com -> ns1.przyklad.com`
7. **SRV Record**: Określa port dla konkretnych usług.
	- Przykład: `_sip._tcp.przyklad.com -> 10 60 5060 sipserver.przyklad.com`
8. **PTR Record**: Mapuje adres IP na domenę (odwrotne wyszukiwanie DNS).
	- Przykład: `192.168.1.1 -> www.przyklad.com`

Te rekordy zapewniają poprawne trasowanie i dostarczanie ruchu internetowego.

![[Pasted image 20240719171203.png]]

MXToolbox to narzędzie online, które oferuje różne usługi związane z DNS, takie jak sprawdzanie rekordów MX (Mail Exchange), które identyfikują serwery pocztowe odpowiedzialne za odbieranie e-maili dla domeny. Umożliwia diagnozowanie problemów z dostarczaniem e-maili, weryfikację rekordów DNS, sprawdzanie czarnych list (DNSBL) oraz mierzenie wydajności odpowiedzi serwerów. Dzięki MXToolbox można skutecznie zarządzać i analizować konfigurację serwerów pocztowych oraz poprawić bezpieczeństwo i niezawodność usług e-mail.


### References:
https://www.youtube.com/watch?v=7lxgpKh_fRY
https://www.youtube.com/watch?v=e48AyJOA9W8
https://www.youtube.com/watch?v=YV5tkQYcvfg
https://mxtoolbox.com/ 
---



