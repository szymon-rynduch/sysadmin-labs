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

