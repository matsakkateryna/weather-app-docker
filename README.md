# Weather App – React + Docker + AWS

Aplikacja pogodowa stworzona w **React + TypeScript**, z wykorzystaniem **Docker**, **GitHub Actions (CI)** oraz wdrożona na **AWS S3 (Static Website Hosting)**.
Demo aplikacji (AWS S3):
http://weather-app-008457818211.s3-website-us-east-1.amazonaws.com/


## Wymagania

- Node.js (wersja 18 lub nowsza)
- npm


## Uruchomienie lokalne bez Dockera

### 1. Klonowanie repozytorium

```bash
git clone https://github.com/matsakkateryna/weather-app-docker.git
cd weather-app
```
## Instalacja zależności

```bash
npm install
```

### Tryb deweloperski

```bash
npm run dev
```

Aplikacja będzie dostępna pod adresem: http://localhost:5173

## Uruchomienie aplikacji w Dockerze

### Budowanie obrazu Dockera

```bash
docker build -t weather-app .
```
### Uruchomienie kontenera

```bash
docker run -p 8080:80 weather-app
```

Aplikacja będzie dostępna pod adresem: http://localhost:8080

## CI – GitHub Actions

Projekt zawiera workflow GitHub Actions, który:
	•	uruchamia się przy każdym push na branch main
	•	buduje obraz Dockera
	•	sprawdza poprawność aplikacji

## Deployment na AWS S3

Aplikacja została:
	1.	Zbudowana lokalnie (npm run build)
	2.	Wgrana do Amazon S3
	3.	Udostępniona jako Static Website Hosting

  Publiczny adres aplikacji: http://weather-app-008457818211.s3-website-us-east-1.amazonaws.com/

## Konfiguracja API pogodowego

Aplikacja domyślnie używa danych testowych (mock). Aby korzystać z prawdziwych danych pogodowych:

1. Zarejestruj się na [OpenWeatherMap](https://openweathermap.org/api)
2. Uzyskaj darmowy klucz API
3. Otwórz plik `src/api/weatherApi.ts`
4. Zamień `YOUR_API_KEY_HERE` na swój klucz API:

```typescript
const API_KEY = 'twój_klucz_api';
```

## Funkcjonalności

### Podstawowe
- Lista 6 polskich miast na stronie głównej
- Szczegóły pogody dla każdego miasta:
  - Aktualna temperatura
  - Ikona warunków pogodowych
  - Prognoza na 5 dni
  - Prawdopodobieństwo opadów, ich rodzaj i ilość
  - Prędkość i kierunek wiatru
  - Stopień zachmurzenia

### Dodatkowe
- Zmiana jednostek temperatury (Celsjusz/Fahrenheit/Kelvin)
- Wyszukiwanie miast po nazwie
- Oznaczanie ulubionych miast (ikona gwiazdki)
- Osobna strona z ulubionymi miastami
- Zapisywanie ustawień w localStorage (jednostki i ulubione)
- Integracja z OpenWeatherMap API

## Technologie

- React 19
- TypeScript
- Vite
- Docker
- GitHub Actions (CI)
- AWS S3 (Static Website Hosting)
- OpenWeatherMap API

## Struktura projektu (skrót)

```
weather-app/
├── public/
├── src/
├── .github/workflows/
├── Dockerfile
├── README.md
└── package.json
```

