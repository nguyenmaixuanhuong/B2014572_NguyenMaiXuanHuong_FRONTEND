<template>
  <div class="page">
    <h4 class="text-center text-danger">Thêm liên hệ mới </h4>
    <AddContactForm @submit:contact="addContact"></AddContactForm>
    <p class="text-success">{{ message }}</p>
  </div>
</template>
<script>
import AddContactForm from "@/components/AddContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    AddContactForm,
  },
  data() {
    return {
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Thêm liên hệ thành công";
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.message = "";
  },
};
</script>
