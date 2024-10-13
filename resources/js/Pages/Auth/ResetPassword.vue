<script setup>
import { useForm } from '@inertiajs/vue3';
import Container from '../../Components/Container.vue';
import InputField from '../../Components/InputField.vue';
import PrimaryButton from '../../Components/PrimaryButton.vue';
import Title from '../../Components/Title.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';

const props = defineProps({
    token: String,
    email: String,
})

const form = useForm({
    token: props.token,
    email: props.email,
    password: "",
    password_confirmation: "",
});

const submit = () => {
    form.post(route('password.update'), {
        onFinish: () => form.reset("password", "password_confirmation"),
    });
};
</script>

<template>

    <Head title="- Reset Password" />
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <Title>Enter your new password</Title>
        </div>

        <!-- Errors messages -->
        <ErrorMessages :errors="form.errors" />

        <form @submit.prevent="submit" class="space-y-6">
            <InputField label="Email" icon="at" v-model="form.email" />
            <InputField label="Password" type="password" icon="key" v-model="form.password" />
            <InputField label="Confirm Password" type="password" icon="key" v-model="form.password_confirmation" />

            <PrimaryButton :disabled="form.processing">
                Reset Password
            </PrimaryButton>
        </form>
    </Container>
</template>