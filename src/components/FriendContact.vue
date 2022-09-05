<template>
  <li>
    <h2>{{name }}</h2>
    <h2>{{favourite ?  "Favourite":"Not Favourite"}}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavourite">Toggle  favourite</button>
    <button @click="deleteFriend">Delete</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>ID:</strong>
        {{ id }}
      </li>
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
    id:{
      type:String,
      required:true,
    },
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
      // default:true,
      // validator:function(value){
      //   if (typeof(value)===Boolean){
      // return true;
      //   }
      // }
    },
  },
  emits:['toggle-favourite','delete-friend'],
  // {
  //   'toggle-favourite':function(id){
  //     if(id){
  //       return true;
  //     }else{
  //       return false;
  //     }
  //   },
  //  ' delete-friend':true,
  // },
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
      
      },
      fav:this.favourite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      // this.fav = !this.fav;
      // console.log(this.fav)
      this.$emit("toggle-favourite",this.id)
      console.log(this.fav)
    },
    deleteFriend(){
      this.$emit("delete-friend",this.id)
    }
  },
  
  
};
</script>