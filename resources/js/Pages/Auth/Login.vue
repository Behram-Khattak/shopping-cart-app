<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />

        <div v-if="status" class="mb-4 font-medium text-sm text-green-600">
            {{ status }}
        </div>

        <!-- logo -->
        <div class="max-w-screen-xl px-6 grid sm:grid-cols-2 place-items-center h-screen">
            <div class="page-title">
                <h1 class="uppercase text-6xl lg:text-7xl xl:text-8xl text-center sm:w-1/2 font-extrabold text-indigo-500">
                    shopping center
                    <font-awesome-icon class="sm:p-4 text-transparent stroke-[2rem] stroke-indigo-500" icon="fas fa-cart-shopping" />
                </h1>
            </div>
            <!--  -->
            <div class="w-full p-4 overflow-hidden sm:rounded-lg">

                <form @submit.prevent="submit">
                    <!-- form title -->
                    <h2 class="uppercase text-4xl text-center py-4 font-extrabold text-indigo-500">login</h2>

                    <div>
                        <InputLabel for="email" value="Email" />

                        <TextInput
                            id="email"
                            type="email"
                            class="mt-1 block w-full"
                            v-model="form.email"
                            required
                            autofocus
                            autocomplete="username"
                        />

                        <InputError class="mt-2" :message="form.errors.email" />
                    </div>

                    <div class="mt-4">
                        <InputLabel for="password" value="Password" />

                        <TextInput
                            id="password"
                            type="password"
                            class="mt-1 block w-full"
                            v-model="form.password"
                            required
                            autocomplete="current-password"
                        />

                        <InputError class="mt-2" :message="form.errors.password" />
                    </div>

                    <div class="block mt-4">
                        <label class="flex items-center">
                            <Checkbox name="remember" v-model:checked="form.remember" />
                            <span class="ms-2 text-sm text-gray-600">Remember me</span>
                        </label>
                    </div>

                    <div class="mt-4">
                        <div>
                            <Link
                                v-if="canResetPassword"
                                :href="route('password.request')"
                                class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none"
                            >
                                Forgot your password?
                            </Link>
                        </div>

                        <PrimaryButton class="mt-8 w-full" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Log in
                        </PrimaryButton>
                    </div>

                    <div class="text-center pt-8">
                        <Link
                            :href="route('register')"
                            class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none"
                        >
                            Don't Have An Account?
                        </Link>
                    </div>
                </form>
            </div>
        </div>
    </GuestLayout>
</template>
