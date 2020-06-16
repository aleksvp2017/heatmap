<template>
    <MyMap
    :key="mapkey"
    :countryData="stateData"
    highColor="#ff0000"
    lowColor="#aaaaaa"
    countryStrokeColor="#909090"
    defaultCountryFillColor="#dadada"
    /> 
</template>

<script>

import MyMap from './views/MyMap'

export default {
    components: {
        'MyMap': MyMap,
    },
    data() {
        return {
            stateData: {},
            showMap: false,
            mapkey: 1,
        }
    },
    created() {
      this.stateData = {}
      var metricsPorUF = generateMetrics()
      metricsPorUF.map(item => this.stateData['BR-' + item.uf] = item.metric)
      console.log(this.stateData)
      this.showMap = true
      this.mapkey = this.mapkey + 1
  },
}

function generateMetrics(){
  var metricsPorUF = [
    { uf: 'DF', metric: 100},
    { uf: 'SP', metric: 200},
    { uf: 'MG', metric: 110},
    { uf: 'RN', metric: 90},
    { uf: 'SC', metric: 150},
    { uf: 'AM', metric: 50},
    { uf: 'PA', metric: 250},
  ]

  return metricsPorUF
}

</script>