<template>
  
  <div>
    
    <!-- 
    <div v-if="isAuth" id="menu">    
    <router-link class="btn btn-primary" :to="{name: 'auth.login'}">login</router-link>
    <router-link class="btn btn-primary" :to="{name: 'auth.logout'}">logout</router-link>
    <router-link class="btn btn-primary" :to="{name: 'pgtest'}">Pagina de Teste</router-link>
    <router-link class="btn btn-primary" :to="{name: 'dashboard'}">dashboard</router-link>
    </div>
    
    <div>
        <router-view></router-view> 
    </div>
    -->
    
    
    <div class="min-h-full">
        
            <nav  v-if="isAuth"  class="bg-gray-800">
                <div class="px-4 mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="flex items-center justify-between h-16">
                    <div class="flex items-center">
                    <!-- Logo tipo da empresa -->
                    <div class="flex-shrink-0">
                        <img class="w-8 h-8" src="https://tailwindui.com/img/logos/workflow-mark-indigo-500.svg" alt="Workflow">
                    </div>
                    <div class="hidden md:block">
                        <div class="flex items-baseline ml-10 space-x-4">
                        <!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
                        <!-- <a href="#"  aria-current="page"></a> -->
                            <router-link class="px-3 py-2 text-sm font-medium text-white bg-gray-900 rounded-md" :to="{name: 'dashboard'}">Livros</router-link>
                            <!-- <router-link class="px-3 py-2 text-sm font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white" :to="{name: 'auth.login'}">login</router-link> -->
                           <router-link class="px-3 py-2 text-sm font-medium text-white bg-gray-900 rounded-md" :to="{name: 'pgtest'}">Cadastro de livros</router-link>
                           <router-link class="px-3 py-2 text-sm font-medium text-white bg-gray-900 rounded-md" :to="{name: 'caixas'}">Cadastro de Autores</router-link>
                           <router-link class="px-3 py-2 text-sm font-medium text-white bg-gray-900 rounded-md" :to="{name: 'autores'}">Autores</router-link>

                        </div>
                    </div>
                    </div>
                    <div class="hidden md:block">
                    <div class="flex items-center ml-4 md:ml-6">
                        <button type="button" class="p-1 text-gray-400 bg-gray-800 rounded-full hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                        <span class="sr-only">View notifications</span>
                        <!-- Heroicon name: outline/bell -->
                        <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
                        </svg>
                        </button>

                        <!-- Profile dropdown -->
                        <div class="relative ml-3">
                        <div>
                            <button type="button" @click="abrir()" class="flex items-center max-w-xs text-sm bg-gray-800 rounded-full focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white" id="user-menu-button" aria-expanded="false" aria-haspopup="true">
                                <span class="sr-only">Open user menu</span>
                                <img class="w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
                            </button>
                        </div>

                        <!--
                            Dropdown menu, show/hide based on menu state.
                            Entering: "transition ease-out duration-100"
                            From: "transform opacity-0 scale-95"
                            To: "transform opacity-100 scale-100"
                            Leaving: "transition ease-in duration-75"
                            From: "transform opacity-100 scale-100"
                            To: "transform opacity-0 scale-95"
                        -->
                        <div v-if="menuPerfil" class="absolute right-0 w-48 py-1 mt-2 origin-top-right bg-white rounded-md shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none" role="menu" aria-orientation="vertical" aria-labelledby="user-menu-button" tabindex="-1">
                            <!-- Active: "bg-gray-100", Not Active: "" -->
                            
                                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-0">Your Profile</a>
                                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-1">Settings</a>
                                <a href="#" class="block px-4 py-2 text-sm text-gray-700" role="menuitem" tabindex="-1" id="user-menu-item-2"><router-link class="btn btn-primary" :to="{name: 'auth.logout'}">logout</router-link></a>
                            
                        </div>
                        </div>
                    </div>
                    </div>
                    <div class="flex -mr-2 md:hidden">
                    <!-- Mobile menu button -->
                    <button type="button" class="inline-flex items-center justify-center p-2 text-gray-400 bg-gray-800 rounded-md hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white" aria-controls="mobile-menu" aria-expanded="false">
                        <span class="sr-only">Open main menu</span>
                        <!--
                        Heroicon name: outline/menu

                        Menu open: "hidden", Menu closed: "block"
                        -->
                        <svg class="block w-6 h-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                        </svg>
                        <!--
                        Heroicon name: outline/x

                        Menu open: "block", Menu closed: "hidden"
                        -->
                        <svg class="hidden w-6 h-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                    </div>
                </div>
                </div>

                <!-- Mobile menu, show/hide based on menu state. -->
                <div class="md:hidden" id="mobile-menu">
                <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                    <!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
                    <a href="#" class="block px-3 py-2 text-base font-medium text-white bg-gray-900 rounded-md" aria-current="page">Dashboard</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white">Team</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white">Projects</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white">Calendar</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white">Reports</a>
                </div>
                <div class="pt-4 pb-3 border-t border-gray-700">
                    <div class="flex items-center px-5">
                    <div class="flex-shrink-0">
                        <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="">
                    </div>
                    <div class="ml-3">
                        <div class="text-base font-medium leading-none text-white">Tom Cook</div>
                        <div class="text-sm font-medium leading-none text-gray-400">tom@example.com</div>
                    </div>
                    <button type="button" class="flex-shrink-0 p-1 ml-auto text-gray-400 bg-gray-800 rounded-full hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                        <span class="sr-only">View notifications</span>
                        <!-- Heroicon name: outline/bell -->
                        <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
                        </svg>
                    </button>
                    </div>
                    <div class="px-2 mt-3 space-y-1">
                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-400 rounded-md hover:text-white hover:bg-gray-700">Your Profile</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-400 rounded-md hover:text-white hover:bg-gray-700">Settings</a>

                    <a href="#" class="block px-3 py-2 text-base font-medium text-gray-400 rounded-md hover:text-white hover:bg-gray-700">Sign out</a>
                    </div>
                </div>
                </div>
            </nav>

            <header class="bg-white shadow">
                <div class="px-4 py-6 mx-auto max-w-7xl sm:px-6 lg:px-8">
                    <h1 class="text-3xl font-bold text-gray-900">
                        
                    </h1>
                </div>
            </header>

            <main>
                <div class="py-6 mx-auto max-w-7xl sm:px-6 lg:px-8">
                <!-- Replace with your content -->
                <div class="px-4 py-6 sm:px-0">
                    <div>
                        <router-view> </router-view>
                    </div>
                </div>
                <!-- /End replace -->
                </div>
            </main>
    </div>  
  
  </div>
  
</template>

<script>
    
import store from '../store';
    
export default {
    name: 'app',
    data () {
        return {
            menuPerfil: false,
            }
    },
    methods: {
        abrir() {
            this.menuPerfil = this.menuPerfil == false ? true : false;
        }
    },
    computed:{
        isAuth() {
            return store.state.auth.check;
        },
        user() {
            return store.state.auth.user ? store.state.auth.user : {'name': ''}; 
        }
    }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
