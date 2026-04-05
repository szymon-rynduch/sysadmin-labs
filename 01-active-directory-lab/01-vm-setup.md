# 01 - Konfiguracja Maszyny Wirtualnej

## Wymagania wstępne
- Program do wirtualizacji (VirtualBox)
- ISO Windows Server 2022

## Opis procesu
Na samym początku, organizując laboratorium Active Directory, postanowiłem pobrać program do wirtualizacji maszyn — padło na VirtualBox. Następnie przeszedłem do pobrania obrazu ISO Microsoft Windows Server 2022 z Microsoft Evaluation Center.

Kolejnym krokiem było zainstalowanie VirtualBox oraz stworzenie dwóch maszyn wirtualnych:
- **main-server-AD** — serwer z systemem Windows Server 2022, pełniący rolę kontrolera domeny
- **User-AD** — maszyna użytkownika, która zostanie później dołączona do domeny

Tutaj zostawiam link do filmu jak stworzyć taką maszynę wirtualną:
https://www.youtube.com/watch?v=nvdnQX9UkMY&t=256s&pp=ygUraG93IHRvIG1ha2UgYSB2aXJ0dWFsIG1hY2hpbmUgaW4gdmlydHVhbGJveA%3D%3D

Maszyny na początku zalecam uruchamiać osobno ponieważ obie wykorzystują dużo zasobów pamięci. Natomiast po zainstalowaniu i odpowiedniej konfiguracji można te wartości zmiejszyc aby obie działały równocześnie.


## Parametry fizyczne maszyn przed instalacją i po instalacji.(dodać wartości)
