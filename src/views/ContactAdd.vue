<template>
  <div v-if="contact" class="page">
    <h4>Thêm liên hệ</h4>
    <ContactForm :contact="contact" @submit:contact="addContact" />
    <p>{{ message }}</p>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import contactService from "@/services/contact.service";

export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      contact: {},
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        await contactService.create(data);
        this.message = "Thêm liên hệ mới thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {},
};
</script>
