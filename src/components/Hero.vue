<script setup>
import {computed, ref} from "vue";
import desktopHeroImg1 from "../images/desktop-image-hero-1.jpg";
import desktopHeroImg2 from "../images/desktop-image-hero-2.jpg";
import desktopHeroImg3 from "../images/desktop-image-hero-3.jpg";
import mobileHeroImg1 from "../images/mobile-image-hero-1.jpg";
import mobileHeroImg2 from "../images/mobile-image-hero-2.jpg";
import mobileHeroImg3 from "../images/mobile-image-hero-3.jpg";
import Navigation from "@/components/Navigation.vue";

const contentList = [
    {
        label: "Discover innovative ways to decorate",
        description: "We provide unmatched quality, comfort, and style for property owners across the country. \n" +
            "Our experts combine form and function in bringing your vision to life. Create a room in your \n" +
            "own style with our collection and make your property a reflection of you and what you love.",
        desktopImage: desktopHeroImg1,
        mobileImage: mobileHeroImg1
    },
    {
        label: "We are available all across the globe",
        description: "  With stores all over the world, it's easy for you to find furniture for your home or place of business. \n" +
            "  Locally, we’re in most major cities throughout the country. Find the branch nearest you using our \n" +
            "  store locator. Any questions? Don't hesitate to contact us today.",
        desktopImage: desktopHeroImg2,
        mobileImage: mobileHeroImg2
    },
    {
        label: "Manufactured with the best materials",
        description: "  Our modern furniture store provide a high level of quality. Our company has invested in advanced technology \n" +
            "  to ensure that every product is made as perfect and as consistent as possible. With three decades of \n" +
            "  experience in this industry, we understand what customers want for their home and office.",
        desktopImage: desktopHeroImg3,
        mobileImage: mobileHeroImg3
    }]

const currentContentIndex = ref(0)

const currentContent = computed(() => contentList[currentContentIndex.value])
const onChangeContent = async (value) => {
    if (currentContentIndex.value + value > 2) currentContentIndex.value = 0
    else if (currentContentIndex.value + value < 0) currentContentIndex.value = 2
    else currentContentIndex.value += value
}

</script>

<template>
    <div class="container">
        <div class="hero-container">
            <img v-if="currentContent.desktopImage" :src="currentContent.desktopImage" alt="" class="desktop-hero-img">
            <img v-if="currentContent.mobileImage" :src="currentContent.mobileImage" alt="" class="mobile-hero-img">
            <div class="carousel-container">
                <button @click="onChangeContent(-1)"><img src="../images/icon-angle-left.svg" alt=""></button>
                <button @click="onChangeContent(1)"><img src="../images/icon-angle-right.svg" alt=""></button>
            </div>
        </div>
        <Navigation/>
        <header>
            <h1>
                {{ currentContent.label }}
            </h1>
            <p>
                {{ currentContent.description }}
            </p>
            <button>Shop now <img src="../images/icon-arrow.svg" alt=""></button>
        </header>
    </div>
</template>

<style scoped>

.container {
    display: flex;
}

.hero-container {
    flex: 2;
    position: relative;
    object-fit: cover;
}

.hero-container img {
    width: 100%;
    height: 100%;
}

.mobile-hero-img {
    display: none;
}

.carousel-container {
    width: fit-content;
    position: absolute;
    bottom: 0;
    right: -136px;
}

.carousel-container button {
    padding: 2.25rem;
    background: hsl(0, 0%, 0%);
    transition: ease-in 150ms;
    cursor: pointer;
}

.carousel-container button:hover {
    background: hsl(0, 0%, 63%);
}

header {
    padding: 8rem 6rem;
    position: relative;
    flex: 1;
}

header h1 {
    font-size: 4rem;
    margin-bottom: 2rem;
}

header p {
    color: hsl(0, 0%, 63%);
    line-height: 140%;
    margin-bottom: 2rem;
}

header > button {
    letter-spacing: 1rem;
    color: hsl(0, 0%, 0%);
    font-weight: 700;
    text-transform: uppercase;
    align-items: center;
    display: flex;
    column-gap: 2rem;
    cursor: pointer;
}

header > button:hover {
    color: hsl(0, 0%, 63%);
}

@media screen and (max-width: 425px) {
    .container {
        flex-direction: column;
    }

    .carousel-container {
        right: 0;
    }

    header {
        padding: 6rem 2rem;
    }

    header h1 {
        font-size: 3rem;
    }

    .mobile-hero-img {
        display: block;
    }

    .desktop-hero-img {
        display: none;
    }
}
</style>