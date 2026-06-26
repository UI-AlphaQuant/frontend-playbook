## 📌 Google Maps API

| Item     | Description                                  |
| -------- | -------------------------------------------- |
| Provider | :contentReference[oaicite:0]{index=0}        |
| Purpose  | Maps, Places, Directions, Geocoding          |
| Used In  | Delivery Apps, Real Estate, Travel, Tracking |
| Billing  | Pay-As-You-Go + Free Monthly Credit          |

| Common APIs         | Purpose                 |
| ------------------- | ----------------------- |
| Maps JavaScript API | Display Interactive Map |
| Places API          | Search Places           |
| Geocoding API       | Address ⇄ Coordinates   |
| Directions API      | Route Navigation        |
| Distance Matrix API | Travel Distance & Time  |
| Geolocation API     | Detect User Location    |
| Street View API     | Street Images           |

```txt
Google Maps API
├─ Map
├─ Marker
├─ Places
├─ Geocoding
├─ Directions
├─ Distance Matrix
└─ Geolocation
```

```txt
React
  ↓
Google Maps Component
  ↓
API Key
  ↓
Map
  ↓
Marker
  ↓
Places / Directions
```

### Setup (Create API Key)

```txt
Google Cloud Console > Create Project > Enable Maps API > Generate API Key
```

```bash
npm install @react-google-maps/api
```

```tsx
// Basic Map
import { GoogleMap, LoadScript } from "@react-google-maps/api";
export default function App() {
  return (
    <LoadScript googleMapsApiKey="API_KEY">
      <GoogleMap
        center={{
          lat: 23.0225,
          lng: 72.5714,
        }}
        zoom={12}
        mapContainerStyle={{
          width: "100%",
          height: "400px",
        }}
      />
    </LoadScript>
  );
}
```

```tsx
// Marker
import { Marker } from "@react-google-maps/api";
<Marker
  position={{
    lat: 23.0225,
    lng: 72.5714,
  }}
/>;
```

```ts
// User Location
navigator.geolocation.getCurrentPosition((position) => {
  console.log(position.coords.latitude);
  console.log(position.coords.longitude);
});
```

```txt
// Geocoding (Address → Coordinates)
Ahmedabad, Gujarat
       ↓
23.0225, 72.5714

https://maps.googleapis.com/maps/api/geocode/json?address=Ahmedabad&key=API_KEY
```

---
