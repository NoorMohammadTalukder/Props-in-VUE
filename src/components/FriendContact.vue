<template>
  <li>
    <h2>{{name }}</h2>
    <h2>{{fav ?  "Favourite":"Not Favourite"}}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavourite">Toggle  favourite</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
      <!-- <li>
      
        {{favourite ? 'favourite':'Not favourite' }}
      </li> -->
    </ul>
  </li>
</template>

<script>
export default {
  // props:[
  //     'name',
  //     'phoneNumber',
  //     'emailAddress',
   
  // ],
  props:{
    name:{
      type:String,
      required:true,
    },
    phoneNumber:{
      type:String,
      required:true,
    },
    emailAddress:{
      type:String,
      required:true,
    },
    favourite:{
      type:Boolean,
      required:true,
    },
  },
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
        fav:this.favourite,
      },
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      this.fav = !this.fav;
      console.log(this.fav)
    }
  },
  
  
};
</script>