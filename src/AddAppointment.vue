<template>
<div class="col-12 col-md-10 col-lg-7">
    <div class="input-group my-3">
      <input
        id="SearchApts"
        placeholder="Search"
        type="text"
        class="form-control"
        aria-label="Search Appointments"
      >
      </div>
      <div class="card-body" :class="{ 'd-none': hidepanel}">
        <form id="aptForm"
        @submit.prevent="requestAdd"></form>
          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="petName">Pet Name</label>
            <div class="col-md-10">
              <input
                type="text"
                class="form-control"
                name="petName"
                id="petName"
                placeholder="Pet's Name"
                v-model="formData.petName"
              >
              
              
            
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="ownerName">Pet Owner</label>
            <div class="col-md-10">
              <input type="text" class="form-control" id="ownerName" placeholder="Owner's Name"
              v-model="formData.ownerName">
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="aptDate">Date</label>
            <div class="col-md-4">
              <input type="date" class="form-control" id="aptDate"
              v-model="formData.aptTime">
            </div>
            <label class="col-md-2 col-form-label text-md-right" for="aptTime">Time</label>
            <div class="col-md-4">
              <input type="time" class="form-control" name="aptTime" id="aptTime">
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 text-md-right" for="aptNotes">Apt. Notes</label>
            <div class="col-md-10">
              <textarea
                class="form-control"
                rows="4"
                cols="50"
                name="aptNotes"
                id="aptNotes"
                placeholder="Appointment Notes"
                v-model="formData.aptNotes"
              ></textarea>
            </div>
          </div>

      <div class="input-group-append">
        <button
          type="button"
          class="btn btn-primary dropdown-toggle"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
        >
          Sort by
          <span class="caret"></span>
        </button>

        <div class="dropdown-menu dropdown-menu-right">
          <a href="#" class="dropdown-item d-flex justify-content-between" id="petName">
            Pet Name
            <font-awesome-icon icon="check"/>
          </a>

          <a class="dropdown-item d-flex justify-content-between" href="#" id="aptDate">
            Date
            <font-awesome-icon icon="check"/>
          </a>

          <a href="#" class="dropdown-item d-flex justify-content-between" id="ownerName">
            Owner
            <font-awesome-icon icon="check"/>
          </a>

          <div class="dropdown-divider" role="separator"></div>

          <a
            class="dropdown-item d-flex justify-content-between"
            href="#"
            id="asc"
          >
            Asc
            <font-awesome-icon icon="check"/>
          </a>

          <a
            class="dropdown-item d-flex justify-content-between"
            href="#"
            id="desc"
          >
            Desc
            <font-awesome-icon icon="check"/>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
export default {
  name: "AddAppointment",
  data(){
    return{
        formData: [],
        hidepanel: true
    }
  },
  components: {
    FontAwesomeIcon
  },
  methods: {
    requestAdd: function() {
        this.formData = {
            petName: this.formData.petName,
            petOwner: this.formData.pet0,
            aptDate: this.formData.aptDate + ' '+ this.formData.aptTime,
            aptNotes: this.formData.aptNotes,
        };
        this.$emit("add", this,formData);
        this.formData=[];
        this.hidepanel = true;
    }
  }
};
</script>