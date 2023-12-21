<!-- <template>
    <div class="container">
        <slot />
        <footer>&copy; ura.com</footer>     
    </div> 
</template>
<style>
footer {
    background-color: bisque;
    color: azure;
}
</style> -->
<template>
<v-app>
    <AppHeader />
    <SideNav />
    <v-main>
    <v-container>
        <slot />
    </v-container>
    </v-main>
    <AppFooter />
</v-app>
</template>