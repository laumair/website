<script>
    import { onMount } from "svelte";
    import * as am5 from "@amcharts/amcharts5";
    import * as am5map from "@amcharts/amcharts5/map";
    import geoData from "@amcharts/amcharts5-geodata/worldLow";
    import responsiveTheme from "@amcharts/amcharts5/themes/Responsive";
    import countriesData from "@amcharts/amcharts5-geodata/data/countries2";

    import Content from "./content.json";

    let map;

    onMount(() => {
        // Create root and chart
        const root = am5.Root.new(map);

        // Set theme
        root.setThemes([responsiveTheme.new(root)]);

        const chart = root.container.children.push(
            am5map.MapChart.new(root, {
                minZoomLevel: 1,
                maxZoomLevel: 3,
                projection: am5map.geoMercator(),
            })
        );

        var polygonSeries = chart.series.push(
            am5map.MapPolygonSeries.new(root, {
                geoJSON: geoData,
                exclude: ["AQ"],
            })
        );

        polygonSeries.mapPolygons.template.setAll({
            tooltipText: "{name}",
            templateField: "polygonSettings",
        });

        polygonSeries.mapPolygons.template.states.create("hover", {
            fill: am5.color(0x84ade9),
            stroke: am5.color(0x84ade9),
        });

        const countries = prepareCountriesData();

        polygonSeries.data.setAll(countries);
    });

    function prepareCountriesData() {
        return Object.keys(countriesData).map((id) => {
            const country = countriesData[id];

            if (Content.visitedCountries.includes(country.country)) {
                return {
                    id,
                    polygonSettings: {
                        fill: am5.color(0x008000),
                    },
                };
            }

            return {
                id,
                polygonSettings: {
                    fill: am5.color(0xa6a6a6),
                },
            };
        });
    }
</script>

<div bind:this={map} class="wrapper" />

<style>
    .wrapper {
        width: 100%;
        height: 30vh;
    }

    @media (min-width: 768px), (min-width: 1024px), (min-width: 1200px)   {
        .wrapper {
            height: 100vh;
        }
    }
</style>
