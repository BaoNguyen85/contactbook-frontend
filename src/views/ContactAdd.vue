<template>
    <div class="add-form">
        <div>
            <h4>Thêm Liên hệ</h4>
        </div>

        <div>
            <h5>Liên hệ đã được thêm thành công.</h5>
            <button class="btn btn-success">Thêm</button>
        </div>
    </div>
</template>

<script>
import ContactService from "../services/contact.service";
import ContactForm from "../components/ContactForm";

export default {
    name: "ContactAdd",
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: null,
            message: "",
        };
    },
    methods: {
        async createContact(data) {
            const [error, response] = await this.handle(ContactService.create(data));
            if (error) {
                console.log(error);
            } else {
                this.contact = response.data;
                console.log(response.data);
            }
        },
    },
    mounted() {
        this.message = "";
        this.getContact(this.$route.params.id);
    },
};
</script>

<style>
.edit-form {
    max-width: 400px;
    margin: auto;
}
</style>
