<script setup>
import { Link } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';

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
        <header class="max-w-screen-xl mx-auto px-4 border-b-2 pb-5">
            <!-- nav logo -->
            <!-- <ApplicationLogo /> -->

            <!-- nav items -->
            <nav class="bg-white border-gray-200 dark:bg-gray-900">
                <div class="flex flex-wrap items-center justify-between">
                    <ApplicationLogo />

                    <button data-collapse-toggle="navbar-default" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600" aria-controls="navbar-default" aria-expanded="false">
                        <span class="sr-only">Open main menu</span>
                        <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"/>
                        </svg>
                    </button>

                    <div class="hidden w-full md:block md:w-auto" id="navbar-default">
                        <ul v-if="props.canLogin" class="font-medium flex flex-col sm:items-center p-4 md:p-0 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
                            <!-- unauthenticated links -->
                            <li>
                                <Link
                                    :href="route('home')"
                                    :class="{'bg-indigo-700 text-white md:bg-transparent md:text-indigo-700': $page.component === 'Frontend/Home'}"
                                    class="block py-2 px-3 rounded md:bg-transparent md:text-gray-900 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:text-indigo-500" aria-current="page">
                                        Home
                                    <font-awesome-icon
                                        :class="{'stroke-white sm:stroke-indigo-500': $page.component === 'Frontend/Home'}"
                                        class="text-transparent stroke-[2rem] stroke-indigo-500 pl-1" icon="fas fa-home"
                                    />
                                </Link>
                            </li>
                            <!--  -->
                            <li>
                                <Link
                                    :href="route('frontend.products')"
                                    :class="{'bg-indigo-700 text-white md:bg-transparent md:text-indigo-700': $page.component === 'Frontend/Products'}"
                                    class="block py-2 px-3 md:text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:hover:text-indigo-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">

                                    Products
                                    <font-awesome-icon
                                        :class="{'stroke-white sm:stroke-indigo-500': $page.component === 'Frontend/Products'}"
                                        class="text-transparent stroke-[2rem] stroke-indigo-500 pl-1" icon="fas fa-box"
                                    />
                                </Link>
                            </li>

                            <!-- shopping cart icon -->
                            <li>
                                <Link
                                    :href="route('frontend.shopping-cart')"
                                    :class="{'bg-indigo-700 text-white md:bg-transparent md:text-indigo-700': $page.component === 'Frontend/ShoppingCart'}"
                                    class="block py-2 px-3 md:text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:hover:text-indigo-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">

                                    Cart
                                    <font-awesome-icon
                                        :class="{'stroke-white md:text-indigo-700': $page.component === 'Frontend/ShoppingCart'}"
                                        class="text-transparent hover:text-indigo-500 stroke-[2rem] pl-1 stroke-indigo-500" icon="fas fa-cart-shopping"
                                    />
                                </Link>
                            </li>

                            <!-- dashboard link after authenticating -->
                            <li v-if="$page.props.auth.user">
                                <Link
                                    :href="route('dashboard')"
                                    :class="{'bg-indigo-700 text-white md:bg-transparent md:text-indigo-700': $page.component === '/Dashboard'}"
                                    class="block py-2 px-3 md:text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:hover:text-indigo-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">
                                        Dashboard
                                    <font-awesome-icon
                                        :class="{'stroke-white sm:stroke-indigo-500': $page.component === '/Dashboard'}"
                                        class="text-transparent stroke-[2rem] stroke-indigo-500 pl-1" icon="fas fa-dashboard"/>
                                </Link>
                            </li>
                            <!-- authenticated links -->
                            <template v-else>
                                <!-- dropdown -->
                                <Dropdown>
                                    <template #trigger>
                                        <span class="inline-flex rounded-md">
                                            <button
                                                type="button"
                                                class="border-2 my-4 sm:my-0 w-10 h-10 rounded-full border-indigo-200 hover:border-indigo-500 focus:ring-2 focus:ring-indigo-500"
                                            >
                                                <font-awesome-icon icon="fas fa-user" class="text-transparent stroke-[4rem] stroke-indigo-500"/>
                                            </button>
                                        </span>
                                    </template>

                                    <template #content>
                                        <DropdownLink :href="route('login')" class="hover:bg-indigo-500 hover:text-white">
                                            Login
                                        </DropdownLink>
                                        <!--  -->
                                        <DropdownLink :href="route('register')" class="hover:bg-indigo-500 hover:text-white">
                                            Register
                                        </DropdownLink>
                                    </template>
                                </Dropdown>
                                <!-- <li>
                                    <Link :href="route('login')" class="block py-2 px-3 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:hover:text-indigo-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">
                                        Login
                                    </Link>
                                </li>
                                <li>
                                    <Link :href="route('register')" class="block py-2 px-3 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-indigo-700 md:p-0 dark:text-white md:dark:hover:text-indigo-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">
                                        Register
                                    </Link>
                                </li> -->
                            </template>
                        </ul>
                    </div>
                </div>
            </nav>
        </header>
    </div>
</template>
