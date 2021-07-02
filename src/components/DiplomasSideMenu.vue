<template>
    <nav id="DiplomasSideMenu">
        <slot name="items">

        </slot>
    </nav>
</template>

<script>
    export default {
        name: "DiplomasSideMenu",
        components: {

        },
    }
</script>

<style scoped>
    nav#DiplomasSideMenu {
        width: 207px;

        display: flex;

        background-color: var(--color-contrast-gray);

        padding-top: 40px;
        /* padding-left: 20px; */

        border-right: 2px solid rgba(100, 100, 100, 0.2);

        height: 700px;

        margin-right: 20px;
    }
</style>