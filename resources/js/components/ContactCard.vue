<template>
   <div class="container">
      <div class="card p-3" style="max-width: 540px;">
         <div class="row no-gutters">
            <div class="col-md-3 col-lg-3">
               <img :src="contact.image" class="rounded my-auto" width="85" height="110" />
            </div>
            <div class="col-md-6">
               <div class="card-body">
                  <h4 class="card-title">{{ contact.name }}</h4>
                  <p class="card-text mb-0">{{ contact.number }}</p>
                  <p class="card-text">{{ contact.email }}</p>
               </div>
            </div>
            <div class="col-md-3">
               <button @click="selectDetails(contact.id)" class="btn btn-outline-primary mt-1 mb-3"><i class="fa fa-pencil"></i></button>
               <button @click="deleteContact(contact.id)" class="btn btn-danger"><i class="fa fa-trash"></i></button>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   props: {
      contact: { type: Object, required: true }
   },
   methods: {
      selectDetails(id) {
         localStorage.setItem('selectedIdDetails', id)
         window.location.href = '/contact-details'
      },
      deleteContact(id) {
         let result = confirm(`Do you want to delete ${this.contact.name}'s contact?`)
         if(result) {
            let contacts = JSON.parse(localStorage.getItem('contacts'))
            let index = contacts.findIndex(c => c.id === id)
            
            contacts.splice(index, 1)
            localStorage.setItem('contacts', JSON.stringify(contacts))

            this.$root.$emit('contactDeleted')
         }
      },
   },
}
</script>