<template>
    <section>
      <form @submit.prevent="formSubmit">
        <h1>Add New friend Details</h1>
        <div>
            <label>Name</label>
            <input type="text" v-model="enteredName">
        </div>
        <div>
            <label>Phone</label>
            <input type="text" 
            v-model="enteredPhone">
        </div>
        <div>
            <label>Email</label>
            <input type="text" v-model="eneteredEmail">
        </div>
        <div>
            <button>Add Friend</button>
        </div>
      </form>
    </section>
</template>

<script>
    export default{
        data(){
            return{
                enteredName:"",
                enteredPhone:"",
                eneteredEmail:""
            }
        },
        emits:["add-friend"],
        methods:{
            formSubmit(){
                console.log(this.enteredName);
                console.log(this.enteredPhone);
                console.log(this.eneteredEmail);
                this.$emit("add-friend",this.enteredName,this.enteredPhone,this.eneteredEmail);
                
                this.enteredName="";
                this.enteredPhone="";
                this.eneteredEmail="";
            }
        }
    }
</script>
