<template>
    <footer>
        <div class="footerdiv">
            <span>{{result.current.humidity}} %</span>
            <strong> Humidity </strong>
        </div>

         <div class="footerdiv">
             <span>{{result.current.wind_kph}} km/h</span>
            <strong> WindSpeed </strong>
        </div>

         <div class="footerdiv">
             <span>{{result.current.feelslike_c}} ºC</span>
            <strong> Feels Like </strong>
        </div>
    </footer>
</template>

<script>

export default {
  data: () => ({

  }),
  props:{
    result: []
  }
}

</script>