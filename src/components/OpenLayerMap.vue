<template>
  <div id="map" class="map ion-justify-content-center"></div>
</template>

<script>
import "ol/ol.css";
import Map from "ol/Map";
import View from "ol/View";
import TileLayer from "ol/layer/Tile";
import OSM from "ol/source/OSM";
import { useGeographic } from "ol/proj";
import Point from "ol/geom/Point";
import Feature from "ol/Feature";
import VectorSource from "ol/source/Vector";
import VectorLayer from "ol/layer/Vector";
export default {
  name: "OpenMap",
  data() {
    return {
      mainMap: null,
      initialCoordinates: [-47, -15],
    };
  },
  mounted() {
    this.myMap();
  },
  methods: {
    myMap() {
      useGeographic();
      this.mainMap = new Map({
        layers: [
          new TileLayer({
            source: new OSM(),
          }),
          new VectorLayer({
            source: new VectorSource({
              features: [new Feature(new Point(this.initialCoordinates))],
            }),
          }),
        ],
        target: "map",
        view: new View({
          center: this.initialCoordinates,
          zoom: 12,
        }),
      });
      setTimeout(() => {
        this.mainMap.updateSize();
      }, 500);
    },
  },
};
</script>

<style>
.map {
  min-height: 100px;
  height: 100%;
  width: 100%;
}
</style>