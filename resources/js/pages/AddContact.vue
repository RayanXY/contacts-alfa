<template>
   <div class="p-3">
      <h2>Add Contact</h2>
      <div class="mb-2">
         <span>Name:</span>
         <input type="text" v-model="name" placeholder="Name">
      </div>
      <div class="mb-2">
         <span>Number:</span>
         <input type="text" v-model="number" placeholder="Number">
      </div>
      <div class="mb-2">
         <span>E-mail:</span>
         <input type="email" v-model="email" placeholder="E-mail">
      </div>
      <div class="mb-2">
         <span>Image:</span>
         <input type="file" @change="imageChange" placeholder="E-mail" accept="image/*">
      </div>

      <button @click="save">Save</button>
   </div>
</template>

<script>
export default {
   data() {
      return {
         name: '',
         number: '',
         email: '',
         image: '',
      }
   },
   methods: {
      imageChange(e) {
         this.createImage(e.target.files[0])
      },
      save() {
         let contact = {
            name: this.name,
            email: this.email,
            image: this.image,
            number: this.number,
         }

         if(localStorage.getItem('contacts') === null) {
            let contacts = []
            contacts.push(contact)
            localStorage.setItem('contacts', JSON.stringify(contacts))
         } else {
            let contacts = JSON.parse(localStorage.getItem('contacts'))
            contacts.push(contact)
            localStorage.setItem('contacts', JSON.stringify(contacts))
         }
      },
      createImage(img) {
         let reader = new FileReader()
         reader.onload = (e) => {
            this.image = e.target.result
         }
         reader.readAsDataURL(img)
      }
   }
}
</script>
