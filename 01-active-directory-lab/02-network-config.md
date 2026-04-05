## **Konfiguracja sieciowa**

**1. Zmiana trybu sieci w VirtualBox**

Jeśli posiadamy zainstalowane już dwie maszyny kolejnym krokiem powinna być zastosowana zmiana ustawień sieciowych w VirtualBox do poszczególnej maszyny.

Wchodząc w ustawienia sieciowe w WirtualBox, natkniemy się na kilka rodzajów połączeń:

<img width="220" height="163" alt="image" src="https://github.com/user-attachments/assets/9bf03d20-44da-4909-bbee-22ed4f536064" />

**NAT** — maszyna ma dostęp do internetu przez hosta, ale jest przed nim ukryta. Inne urządzenia w sieci jej nie widzą.

**Mostkowana karta sieciowa (Bridged)** — maszyna dostaje własne IP od routera i jest widoczna w sieci jak fizyczne urządzenie. **Używamy tego w naszym lab.**

**Sieć wewnętrzna (Internal Network)** — maszyny wirtualne komunikują się tylko między sobą. Host ich nie widzi, brak internetu. Dobry do izolowanych labów.

**Karta sieci izolowanej (Host-only)** — maszyna komunikuje się tylko z hostem. Brak internetu, brak dostępu do sieci lokalnej.

**Rodzajowy sterownik** — zaawansowany tryb, rzadko używany w domowych labach.

**Sieć NAT** — podobny do NAT, ale maszyny wirtualne mogą się między sobą komunikować.

**Cloud Network [EXPERIMENTAL]** — funkcja eksperymentalna, nie używać w labach.
Niepodłączona — brak karty sieciowej, maszyna odcięta od sieci.


**DLACZEGO UŻYWAMY TYPU SIECI MOSTKOWEJ KARTY SIECIOWEJ?**

Używamy jej dlatego, ponieważ pozwala maszynie wirtualnej otrzymać własny adres IP od routera i samodzielnie komunikować się z innymi urządzeniami w sieci — co w przypadku Active Directory jest kluczowe, gdyż kontroler domeny musi być widoczny dla wszystkich maszyn w domenie.




**2. Ustawienie statycznego adresu IP na serwerze**

Wchodzimy w naszą maszynę wirtualną na której zainstalowaliśmy Windows Serwer aby ustawić odpowiednie IP dla naszego głównego serwera.

<img width="369" height="57" alt="image" src="https://github.com/user-attachments/assets/08e910f8-9a73-4ff3-8676-14837e59c6b7" />

**⚠️ WAŻNA UWAGA — ROUTER DOMOWY Z DHCP**
Pracuję z routerem domowym, gdzie adresy IP przydzielane są automatycznie przez serwer DHCP. 
Aby wyznaczyć bezpieczny statyczny IP dla serwera należy:

1. Sprawdzić zakres sieci wpisując `ipconfig` w CMD na swoim PC
2. Zapamiętać: adres IP, maskę podsieci oraz bramę domyślną
3. Wybrać adres IP poza zakresem DHCP routera (zazwyczaj niskie numery np. `192.168.1.10`)
4. Zweryfikować czy adres jest wolny: `ping 192.168.1.10` — brak odpowiedzi = adres wolny.CLS

<img width="891" height="427" alt="image" src="https://github.com/user-attachments/assets/378544cd-65b9-4f2d-8179-420e715bf612" />

Osobiście wziąłem liczbę wysoką np.200 aby uniknąć zbędnych probelmów z konfiguracją.
Następnie zapisałem sobie wyżej wymienione rzeczy czyli: adres IP, maskę podsieci oraz bramę domyślną

Zweryfikowany został adres IP poleceniem PING ping 192.168.x.x

Nastepnie przechodzimy do panelu sterowania na naszej maszynie z Windows Server:
-> Network and Internet
-> Network and Sharing Center
-> Klikamy w niebieski link z nazwą naszej sieci
-> Klikamy właściwości
-> Następnie kilkamy na Internet Protocol Version 4 (TCP/IP) -> Właściwości 
-> Klikamy Use the Following IP Address (Czyli w tym momencie przypisujemy naszemu serwerowi statyczny IP address)
-> Klikamy na pole Use the following DNS Serwer address

Po poprawnym skonfigurowaniu właściwości (zdjęcie poniżej)

<img width="758" height="573" alt="image" src="https://github.com/user-attachments/assets/7b02edc1-ddad-4dec-a838-81634a706554" />

-> Klikamy okay i w tym momencie mamy przydzielony statyczny adres IP do naszego serwera AD
