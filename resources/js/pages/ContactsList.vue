<template>
   <div class="p-3">
      <h2>Contacts List</h2>

      <div v-if="contacts.length > 0">
         <p>Name: {{ contacts[0].name }}</p>
         <p>Number: {{ contacts[0].number }}</p>
         <p>E-mail: {{ contacts[0].email }}</p>
         Img: <img :src="contacts[0].image" width="100" height="150"/>
      </div>

      <div v-else>
         Empty contact list
      </div>

      <a href="/add-contact">Add Contact</a>
      
   </div>
</template>

<script>
export default {
   data() {
      return {
         contacts: ''
      }
   },
   mounted() {
      if(localStorage.getItem('contacts') !== null) {
         this.contacts = JSON.parse(localStorage.getItem('contacts'))
      }
   },
};
</script>
