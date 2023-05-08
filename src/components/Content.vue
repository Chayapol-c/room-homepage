<script setup>

</script>

<template>
    <div class="content-container">
        <img src="../images/image-about-dark.jpg" alt="">
        <main>
            <article>
                <h2>About our furniture</h2>
                <p>
                    Our multifunctional collection blends design and function to suit your individual taste.
                    Make each room unique, or pick a cohesive theme that best express your interests and what
                    inspires you. Find the furniture pieces you need, from traditional to contemporary styles
                    or anything in between. Product specialists are available to help you create your dream space.
                </p>
            </article>
        </main>
        <img src="../images/image-about-light.jpg" alt="">
    </div>
</template>

<style scoped>

.content-container {
    display: flex;
}
main {
    align-self: center;
}
article {
    padding: 5rem;
}
article h2 {
    font-size: 1.5rem;
    letter-spacing: 0.5rem;
    margin-bottom: 1rem;
    text-transform: uppercase;
}
article p {
    color: hsl(0, 0%, 63%);
    line-height: 140%;
}

@media screen and (max-width: 425px) {
    .content-container {
        flex-direction: column;
    }

    article {
        padding: 4rem 2rem;
    }

    article h2 {
        font-size: 1.1rem;
    }
}
</style>