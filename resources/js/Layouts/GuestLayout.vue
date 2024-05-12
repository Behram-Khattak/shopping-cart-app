<script setup>
import FrontendHeader from '@/Components/FrontendHeader.vue';
import FrontendFooter from '@/Components/FrontendFooter.vue';
import Breadcrumbs from '@/Components/Breadcrumbs.vue';
import { Link } from '@inertiajs/vue3';

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
    <div class="flex flex-col sm:justify-center items-center py-6">
        <!-- header -->
        <FrontendHeader :canLogin :canRegister />

        <!-- breadcrumbs -->
        <!-- <Breadcrumbs /> -->

        <!-- main content -->
        <slot />

        <!-- footer -->
        <FrontendFooter />
    </div>
</template>
