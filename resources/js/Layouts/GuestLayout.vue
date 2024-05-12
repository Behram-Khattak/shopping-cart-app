<script setup>
import FrontendHeader from '@/Components/FrontendHeader.vue';
import FrontendFooter from '@/Components/FrontendFooter.vue';
import Breadcrumbs from '@/Components/Breadcrumbs.vue';
import { usePage } from '@inertiajs/vue3';
import { Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});

// get the current page url
const currentUrl = () => {
    return usePage().component;
};
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center py-6">
        <!-- header -->
        <FrontendHeader
            v-if="currentUrl() !== 'Auth/Login' && currentUrl() !== 'Auth/Register'"
            :canLogin
            :canRegister
        />

        <!-- breadcrumbs -->
        <!-- <Breadcrumbs /> -->

        <!-- main content -->
        <slot />

        <!-- footer -->
        <FrontendFooter />
    </div>
</template>
