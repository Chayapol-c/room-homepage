<script setup>

import {ref, watch} from "vue";

const isShowMobileMenu = ref(false)

watch(isShowMobileMenu, (newValue) => {
    const body = document.querySelector("body")
    if (newValue) {
        body.style.overflow = "hidden"
    } else {
        body.style.overflow = "unset"
    }
})

</script>

<template>
    <nav>
        <button @click="isShowMobileMenu = true">
            <img src="../images/icon-hamburger.svg" alt="mobile-menu" class="mobile-icon">
        </button>
        <img src="../images/logo.svg" alt="logo">

        <ul class="desktop-menu">
            <li>home</li>
            <li>shop</li>
            <li>about</li>
            <li>contact</li>
        </ul>
        <div class="mobile-menu" v-if="isShowMobileMenu">
            <button class="close-btn" @click="isShowMobileMenu = false">
                <img src="../images/icon-close.svg" alt="close-icon">
            </button>
            <ul>
                <li>home</li>
                <li>shop</li>
                <li>about</li>
                <li>contact</li>
            </ul>
        </div>

        <div class="mobile-menu-overlay" v-if="isShowMobileMenu" @click="isShowMobileMenu = false">
        </div>
    </nav>
</template>

<style scoped>
nav {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    column-gap: 3rem;
    padding: 4rem;
}

nav p {
    font-size: 2rem;
    color: hsl(0, 0%, 100%);
}

nav ul {
    list-style: none;
    display: flex;
    column-gap: 2rem;
}

nav ul.mobile-menu {
    display: none;
}

.mobile-icon {
    display: none;
}

nav li {
    color: hsl(0, 0%, 100%);
    cursor: pointer;
    transition: ease-in-out 400ms;
}

nav li:hover {
    text-decoration: underline;
    text-underline-offset: 0.5rem;
}

.mobile-menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100dvw;
    height: 100dvh;
    background: hsla(0, 0%, 0%, 0.4);
    z-index: 10;
}

@media screen and (max-width: 425px) {
    header {
        padding: 6rem 2rem;
    }

    header h1 {
        font-size: 3rem;
    }

    nav {
        padding: 4rem 2rem;
        width: 100%;
        justify-content: center;
    }

    .mobile-icon {
        display: block;
        position: absolute;
        left: 2rem;
        transform: translateY(-7px);
    }

    nav ul.desktop-menu {
        display: none;
    }

    nav .mobile-menu {
        display: flex;
        background: hsl(0, 0%, 100%);
        position: fixed;
        top: 0;
        width: 100%;
        padding: 4rem 2rem;
        z-index: 20;
    }

    .mobile-menu ul {
        margin-left: auto;
        column-gap: 2.5rem;
    }

    .mobile-menu li {
        color: hsl(0, 0%, 0%);
        font-size: 1.5rem;
        font-weight: 800;
    }
}
</style>