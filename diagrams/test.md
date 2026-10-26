# Mermaid Test

```mermaid
graph TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Result 1]
    B -->|No| D[Result 2]
```

# GeoJSON Test

```geojson
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "name": "Test Location",
        "description": "<img src=x onerror=alert(1)>"
      },
      "geometry": {
        "type": "Point",
        "coordinates": [-73.9857, 40.7484]
      }
    }
  ]
}
```
