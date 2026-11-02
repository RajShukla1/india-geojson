# India GeoJSON with the official boundary

GeoJSON and TopoJSON for India, its 28 states and 8 union territories, and world countries, with
**India's boundary drawn to match the Survey of India's official political map** (simplified, not certified survey data): the whole of Jammu & Kashmir (including PoK),
Ladakh (including Gilgit-Baltistan and Aksai Chin) and Arunachal Pradesh.

Many charting libraries and map tiles ship a different boundary for India. Showing an incorrect map of India
can lead to legal trouble in India and complaints from users. These files fix that.

Ready-made maps (PNG, PDF, SVG) of India, every state and the world: **[India Map Hub](https://indiamaphub.pages.dev)**

## Files

| File | What it contains |
| --- | --- |
| [india-states.geojson](india-states.geojson) | 36 state/UT polygons with `name`, `slug`, `abbr`, `type`, `region` |
| [india-states.topojson](india-states.topojson) | Same, as TopoJSON (smaller, shared borders, good for D3) |
| [india-outline.geojson](india-outline.geojson) | Single polygon of India's boundary |
| [world-countries-india-view.geojson](world-countries-india-view.geojson) | All countries, with India drawn by its official boundary |

Coordinates are WGS84 (EPSG:4326), simplified for web use.

## Use it

**D3**
```js
const india = await d3.json('https://raw.githubusercontent.com/YOUR-USERNAME/india-geojson/main/india-states.geojson');
const projection = d3.geoMercator().fitSize([width, height], india);
svg.selectAll('path').data(india.features).join('path').attr('d', d3.geoPath(projection));
```

**Leaflet**
```js
fetch('https://raw.githubusercontent.com/YOUR-USERNAME/india-geojson/main/india-states.geojson')
  .then((r) => r.json())
  .then((data) => L.geoJSON(data).addTo(map));
```

**Python (GeoPandas)**
```python
import geopandas as gpd
india = gpd.read_file('https://raw.githubusercontent.com/YOUR-USERNAME/india-geojson/main/india-states.geojson')
```

Also works with MapLibre/Mapbox, Highcharts, ECharts, Power BI (shape map), Tableau and QGIS.

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit: "India Map Hub (https://indiamaphub.pages.dev), based on data by the DataMeet India community (CC BY 4.0) and Natural Earth".

Sources: [DataMeet India community maps](https://github.com/datameet/maps) (CC BY 4.0) and [Natural Earth](https://www.naturalearthdata.com/).
