<template>
    <div class="modal-center">
      <div>
         <h3>{{ modalHeadline }}</h3>
         <div class="mt-2">
            <p>{{ deleteMessage }}</p>
         </div>
      </div>
      <div>
      <button @click="deleteRecord">
         Delete
      </button>
      <button @click="close">
         Cancel
      </button>
      </div>
   </div>
</template>

<script>
export default {
   name: "modal",
   props: {
      modalHeadline: {
         type: String,
         required: true,
      },
      deleteMessage: {
         type: String,
         required: true,
      },
   },
   methods: {
      close() {
         this.$emit("close");
      },
      deleteRecord() {
         this.$emit("deleteRecordEvent");
      },
   },
};
</script>

<style scoped>
   .modal-center {
      position: absolute;
      margin-top: 250px;
      margin-right: -500px;
      border: 2px gray solid;
      padding: 5px;
   }
</style>