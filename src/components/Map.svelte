<script>
    import { onMount } from 'svelte';
    import Map from 'ol/Map.js';
    import OSM from 'ol/source/OSM.js';
    import TileLayer from 'ol/layer/Tile.js';
    import View from 'ol/View.js';
  
    let map;
  
    onMount(() => {
      map = new Map({
        target: 'map',
        layers: [
          new TileLayer({
            source: new OSM(),
          }),
        ],
        view: new View({
          center: [0, 0],
          zoom: 2,
        }),
      });
    });
  </script>
  
  <style>
    #map {
      width: 100%;
      height: 400px; /* Adjust the height as needed */
    }
  </style>
  
  <div id="map"></div>