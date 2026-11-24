# Malawi malaria and environmental data

Monthly district malaria case counts, population and environmental covariates for January 2005–December 2023: 6,156 rows across 27 districts.

- [Chap CSV](chap_MWI_admin2_monthly.csv)
- [District boundaries](chap_MWI_admin2_monthly.geojson)
- [Data dictionary](chap_MWI_admin2_monthly_schema.json): units, sources, methods and limitations for all 43 columns.

## Sources and licences

The source licences and attribution requirements below apply to the corresponding data in this bundle. Retain these credits and the processing notes when redistributing it, including extracts of the CSV. The bundle does not replace the source terms with a single licence.

| Data | Source and citation | Licence / reuse terms |
| --- | --- | --- |
| Malaria cases | Elling et al. (2025), [Malawi Malaria Incidence 2005–2023](https://doi.org/10.5281/zenodo.17161438). Related study: Elling et al. (2026), [Tropical oceans drive variability in soil moisture and malaria in Malawi](https://doi.org/10.1038/s43856-026-01681-9). | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). |
| Boundaries | National Statistics Office of Malawi / OCHA ROSEA, via [geoBoundaries gbOpen MWI ADM2, revision 9469f09](https://github.com/wmgeolab/geoBoundaries/tree/9469f09/releaseData/gbOpen/MWI/ADM2), boundary year 2020. | [CC BY 3.0 IGO](https://creativecommons.org/licenses/by/3.0/igo/). |
| Population | WorldPop, University of Southampton: Global_2000_2020_1km_UNadj for 2005–2020; Global2 R2025A UA v1, constrained, 1 km for 2021–2023. | [CC BY 4.0; WorldPop reuse guidance](https://www.worldpop.org/faq/). |
| ERA5-Land weather and land variables | Copernicus Climate Change Service / ECMWF, [monthly aggregation by Google Earth Engine](https://developers.google.com/earth-engine/datasets/catalog/ECMWF_ERA5_LAND_MONTHLY_AGGR). Dataset citation: Muñoz Sabater (2019), [ERA5-Land monthly averaged data](https://doi.org/10.24381/cds.68d2bb30). | [Licence to Use Copernicus Products](https://cds.climate.copernicus.eu/licences/licence-to-use-copernicus-products); see the notice below. |
| CHIRPS v3 rainfall | UCSB Climate Hazards Center, [CHIRPS3 repository](https://doi.org/10.15780/G2JQ0P) (2025), accessed 2026-11-24; [Funk et al. (2026)](https://doi.org/10.1038/s41597-026-07096-4). | The [provider's v3 page](https://www.chc.ucsb.edu/data/chirps3) states CC BY 4.0 alongside a public-domain waiver. We retain attribution. |
| Vegetation and land cover | NASA / USGS LP DAAC, [MOD13A3.061](https://doi.org/10.5067/MODIS/MOD13A3.061) and [MCD12Q1.061](https://doi.org/10.5067/MODIS/MCD12Q1.061). | Unrestricted use and redistribution under the [MOD13A3](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD13A3#terms-of-use) and [MCD12Q1](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MCD12Q1#terms-of-use) terms. |
| Surface water | EC JRC / Google, [Global Surface Water yearly history v1.4/v1.5](https://global-surface-water.appspot.com/download); Pekel et al. (2016), [High-resolution mapping of global surface water and its long-term changes](https://doi.org/10.1038/nature20584). | Open access under Copernicus terms; [JRC requires acknowledgement and citation](https://global-surface-water.appspot.com/faq). |
| Elevation and slope | NASA / USGS / JPL-Caltech, [SRTMGL1 v003](https://developers.google.com/earth-engine/datasets/catalog/USGS_SRTMGL1_003), February 2000. | Open data; retain source credit. See the product's terms and [USGS credit guidance](https://www.usgs.gov/information-policies-and-instructions/copyrights-and-credits). |
| ENSO | NOAA Climate Prediction Center, [ERSSTv5 Niño 3.4 monthly anomalies](https://www.cpc.ncep.noaa.gov/data/indices/ersst5.nino.mth.91-20.ascii), 1991–2020 reference period. | [US government public-domain data; credit NOAA/NWS](https://www.weather.gov/disclaimer). |

### Copernicus attribution

The following notice applies to all 17 ERA5-Land-derived columns, including relative humidity:

> Contains modified Copernicus Climate Change Service information (2005-2023).

The European Commission and ECMWF are not responsible for uses of the Copernicus data in this bundle.

## Processing and limitations

- Case values from the authors' processed release are retained, including fractional counts and their 2013–2014 underreporting adjustments. These are not new adjustments by this repository.
- District names were matched to geoBoundaries IDs. Likoma has no case series and is excluded. The authors' crosswalk geometries are not redistributed.
- Environmental grids were aggregated to the supplied district polygons; population was summed over valid cells. Relative humidity was derived from monthly temperature and dewpoint, and slope from elevation. District area and population density were also derived.
- Annual population, land-cover and water values are repeated across months; terrain is static. WorldPop changes product in 2021. The dictionary records quality filters and partial-coverage diagnostics.
- Missing observations remain empty. This is a retrospective dataset; check source availability and reporting lags before using it for forecasting.

The [processing code and methods](https://github.com/edvinstava/open-geo-service/tree/2f77983086cb8f98f00fa24cbec17a05838e308b/examples/malawi_chap) document how the sources were joined and transformed.
