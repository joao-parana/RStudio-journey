# centroids

Para ver o centroids no Mapa use:

```
cd centroids
python -m SimpleHTTPServer 8000
open http://localhost:8000
```

A aplicação foi desenvolvida com o Polymer e o código HTML é basicamente o seguinte:

```html
<h1>Kmeans - Centroids para o Dataset 3D_spatial_network.csv</h1>
<google-map latitude="57.17045473893622" longitude="9.590056302529636" min-zoom="8" max-zoom="9" language="pt" api-key="AIzaSyD3E1D9b-Z7ekrT3tbhl_dy8DCXuIuDDRc">
  <google-map-marker latitude="56.94475450049082" longitude="10.011450686148232" title="56.94475450049082, 10.011450686148232" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="56.74087524874841" longitude="9.582880841078499"  title="56.74087524874841,  9.582880841078499" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="57.41689335486228" longitude="10.009328836752536" title="57.41689335486228, 10.009328836752536" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="56.87092786382778" longitude="8.562589230951302"  title="56.87092786382778, 8.562589230951302" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="56.87101939575067" longitude="9.086677369637345"  title="56.87101939575067, 9.086677369637345" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="57.17045473893622" longitude="9.590056302529636"  title="57.17045473893622, 9.590056302529636" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="57.27896284489639" longitude="11.015994073622913" title="57.27896284489639, 11.015994073622913" draggable="false" drag-events=""></google-map-marker>
  <google-map-marker latitude="57.44979207387094" longitude="10.417310567783787" title="57.44979207387094, 10.417310567783787" draggable="false" drag-events=""></google-map-marker>
</google-map>
```
