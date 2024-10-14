<script setup>
import DeleteAccount from './Sections/DeleteAccount.vue';
import UpdateInfo from './Sections/UpdateInfo.vue';
import UpdatePassword from './Sections/UpdatePassword.vue';

defineProps({
    user: Object,
    status: String
})
</script>

<template>

    <Head title="- Profile" />
    <!-- accept the user prop here in the child component  -->
    <UpdateInfo :user="user" :status="status" />
    <UpdatePassword />
    <DeleteAccount />
</template>