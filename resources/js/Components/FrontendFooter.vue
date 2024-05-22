<script setup>
import { Link } from '@inertiajs/vue3';
</script>
<template>
    <div class="footer-frontend mt-auto">
        <footer class="bg-white rounded-lg dark:bg-gray-800">
            <div class="w-full mx-auto max-w-screen-xl p-4 pb-0 md:flex md:items-center md:justify-between">
                <span class="text-sm text-gray-500 sm:text-center dark:text-gray-400">
                    © 2023 <Link :href="route('home')" class="hover:underline">Shopping Center</Link>.
                    All Rights Reserved.
                </span>
                <ul class="flex sm:px-4 flex-wrap items-center mt-3 text-sm font-medium text-gray-500 dark:text-gray-400 sm:mt-0">
                    <li>
                        <Link :href="route('home')" class="hover:underline me-4 md:me-6">
                            Home
                            <font-awesome-icon class="text-transparent stroke-[2rem] stroke-gray-500 pl-1" icon="fas fa-home" />
                        </Link>
                    </li>
                    <li>
                        <Link :href="route('frontend.products')" class="hover:underline me-4 md:me-6">
                            Products
                            <font-awesome-icon class="text-transparent stroke-[2rem] stroke-gray-500 pl-1" icon="fas fa-box" />
                        </Link>
                    </li>
                </ul>
            </div>
        </footer>
    </div>
</template>
