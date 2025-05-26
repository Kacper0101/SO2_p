# Wielowątkowy serwer czatu

**Autorzy:**  
- Dominik Filipiak (273479)  
- Kacper Kostrzewa (272855)

## Opis projektu

Projekt realizuje prosty, wielowątkowy system czatu działający w architekturze klient-serwer.

Program składa się z dwóch części:
- **Serwer czatu** — nasłuchuje na połączenia od klientów, obsługuje wielu użytkowników jednocześnie, rozsyła otrzymane wiadomości do wszystkich uczestników.
- **Użytkownik czatu** — łączy się z serwerem, umożliwia wpisywanie wiadomości i odbieranie wiadomości od innych użytkowników.

## Wymagania systemowe

- **System operacyjny:** Windows
- **Kompilator:** C++ obsługujący standard C++11 lub nowszy
- **Biblioteka:** `ws2_32.lib`

## Kompilacja i uruchomienie

### Serwer
```bash
g++ server.cpp -o server.exe -lws2_32
.\server.exe
### Klient
```bash
g++ user.cpp -o user.exe -lws2_32
.\user.exe


# Struktura programu
Serwer
- **Inicjalizacja Winsock
- **Utworzenie gniazda serwera TCP i przypisanie do portu
- **Nasłuchiwanie połączeń
- **Akceptowanie klientów i tworzenie dla nich osobnych wątków
- **Obsługa użytkownika:
- **Usuwanie klientów po rozłączeniu

### Klient
- **Inicjalizacja Winsock
- **Utworzenie gniazda TCP
- **Połączenie z serwerem pod adresem IP i portem
- **Wysyłanie nazwy użytkownika
- **Uruchomienie wątku odbierającego wiadomości
- **Pętla główna do wysyłania wiadomości
- **Zamykanie połączenia

# Mechanizmy synchronizacji
Projekt wykorzystuje spinlock do synchronizacji dostępu do współdzielonych zasobów (listy klientów), co zapewnia:
- **Wzajemne wykluczanie się wątków
- **Bezpieczny dostęp do współdzielonych danych
- **Efektywną komunikację między wątkami
