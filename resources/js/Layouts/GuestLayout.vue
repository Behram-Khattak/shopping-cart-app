<script setup>
import FrontendHeader from '@/Components/FrontendHeader.vue';
import FrontendFooter from '@/Components/FrontendFooter.vue';
import Breadcrumbs from '@/Components/Breadcrumbs.vue';
import { usePage } from '@inertiajs/vue3';
import { Link } from '@inertiajs/vue3';
import { onMounted } from 'vue';
import { initFlowbite } from 'flowbite';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});

// initialize components based on data attribute selectors
onMounted(() => {
    initFlowbite();
});
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center py-6">
        <FrontendHeader
            v-if="$page.component !== 'Auth/Login' && $page.component !== 'Auth/Register' && $page.component !== 'Auth/ForgotPassword'"
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
