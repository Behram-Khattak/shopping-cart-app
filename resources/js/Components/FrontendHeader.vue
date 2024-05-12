<script setup>
import { Link } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

const props = defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});
</script>

<template>
    <div class="w-full container mb-8">
        <header class="max-w-screen-xl mx-auto px-4 grid grid-cols-3 items-center border-b-2 pb-5">
            <!-- nav logo -->
            <ApplicationLogo />

            <nav class="-mx-3 flex flex-1 justify-center">
                <Link
                    :href="route('home')"
                    class="rounded-md capitalize font-semibold px-3 py-1 text-gray-500 ring-1 ring-transparent hover:border-2 hover:border-indigo-500 transition hover:text-indigo-500 focus:outline-none dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    home
                    <font-awesome-icon class="text-transparent stroke-[2rem] stroke-indigo-500 pl-1" icon="fas fa-home" size="md" />
                </Link>
                <!-- products nav link -->
                <Link
                    :href="route('frontend.products')"
                    class="rounded-md capitalize font-semibold px-3 py-1 text-gray-500 ring-1 ring-transparent hover:border-2 hover:border-indigo-500 transition hover:text-indigo-500 focus:outline-none dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    products
                    <font-awesome-icon class="text-transparent stroke-[2rem] stroke-indigo-500 pl-1" icon="fas fa-box" size="md" />
                </Link>
            </nav>

            <!-- nav items -->
            <nav v-if="props.canLogin" class="-mx-3 flex flex-1 justify-end">
                <Link
                    :href="route('frontend.shopping-cart')"
                    class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    <font-awesome-icon class="text-transparent hover:text-indigo-500 stroke-[2rem] stroke-indigo-500" icon="fas fa-cart-shopping" size="lg" />
                </Link>

                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    Dashboard
                </Link>

                <template v-else>
                    <Link
                        :href="route('login')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Log in
                    </Link>

                    <Link
                        v-if="props.canRegister"
                        :href="route('register')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Register
                    </Link>
                </template>
            </nav>
        </header>
    </div>
</template>
