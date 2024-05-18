<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import ShoppingCard from '@/Components/ShoppingCard.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});
</script>

<template>
    <GuestLayout :canLogin :canRegister>
        <Head title="Home" />

        <!-- main content shopping card -->
        <div class="container">
            <div class="shopping-card-items max-w-screen-xl mx-auto px-4 py-8">
                <div class="">
                    <h3 class="text-2xl uppercase font-bold text-gray-500">new arrivals</h3>
                    <!-- card items -->
                    <div class="mt-6 grid sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6 sm:mt-8">
                        <!-- shopping card products -->
                        <ShoppingCard />
                    </div>
                </div>
            </div>
        </div>

    </GuestLayout>
</template>
