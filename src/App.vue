<template>
<div id="main-app" class="container">
<h4>{{Title}}</h4>
<font-awesome-icon icon="plus" class="mr-2"/>Add Appointment
</div>
</template>

<script>
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
import axios from "axios";
export default {
  name: "MainApp",
  data: function() {
  return {
  title: "Appointment List",
  appointments: []
    };
  },
  components: {
    FontAwesomeIcon
  },
  mounted(){
    axios.get("./data/appointments.json")
    .then(response => (this.appointments = response.data));
  }
}
</script>

