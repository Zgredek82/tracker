# PWA – Trener Tracker

## Co zostało dodane

- `manifest.webmanifest`: nazwa, kolory, tryb standalone i ikona aplikacji.
- `sw.js`: cache podstawowych plików aplikacji oraz zasobów z CDN po ich pierwszym pobraniu.
- `icons/icon.svg`: wektorowa ikona aplikacji.
- `index.html`: metadane PWA, obsługa safe-area na iPhonie i rejestracja Service Workera.

## Wymagania wdrożenia

Aplikacja musi być dostępna przez HTTPS (albo localhost podczas developmentu). Pliki manifestu, Service Workera i ikony muszą być serwowane z tej samej ścieżki bazowej co aplikacja. Konfiguracja używa ścieżek względnych, więc powinna działać również przy publikacji w podkatalogu, np. GitHub Pages.

## Instalacja na iPhonie

1. Otwórz wdrożony adres aplikacji w Safari.
2. Poczekaj, aż strona załaduje się online przynajmniej raz.
3. Wybierz Udostępnij → Dodaj do ekranu początkowego.
4. Uruchom aplikację z nowej ikony.

## Ważne ograniczenia obecnej wersji

- Pierwsze uruchomienie wymaga internetu, ponieważ React, ReactDOM, Babel i Tailwind nadal są ładowane z CDN. Service Worker zapisuje te zasoby w cache po pierwszym udanym pobraniu, aby umożliwić kolejne uruchomienia offline.
- Nie dodano jeszcze procesu build/bundlingu. Docelowo warto przenieść zależności do lokalnych plików i rozważyć migrację z Babel Standalone do bundlera.
- Dane użytkownika nadal są przechowywane lokalnie w przeglądarce. PWA nie zapewnia synchronizacji ani kopii danych w chmurze.
- Ikona SVG jest używana w manifeście i jako apple-touch-icon; należy zweryfikować jej wygląd po dodaniu do ekranu początkowego na docelowym iPhonie.
- Service Worker nie był uruchomiony w prawdziwej przeglądarce w ramach tej zmiany. Przed scaleniem trzeba sprawdzić instalację, odświeżanie wersji oraz działanie offline po pierwszym pełnym załadowaniu online.

## Test ręczny

- [ ] Otworzyć stronę przez HTTPS w Safari.
- [ ] Dodać ją do ekranu początkowego.
- [ ] Sprawdzić uruchomienie bez paska Safari.
- [ ] Po pierwszym pełnym załadowaniu włączyć tryb samolotowy i uruchomić ponownie.
- [ ] Dodać posiłek offline, zamknąć i ponownie uruchomić aplikację.
- [ ] Przywrócić internet i sprawdzić aktualizację strony po nowym wdrożeniu.
