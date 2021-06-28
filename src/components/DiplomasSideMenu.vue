<template>
    <div id="DiplomasSideMenu">
        <slot name="items">

        </slot>
    </div>
</template>

<script>
    export default {
        name: "DiplomasSideMenu",
        components: {

        },
    }
</script>

<style scoped>
    div#DiplomasSideMenu {
        width: 207px;

        display: flex;

        background-color: var(--color-contrast-gray);

        padding-top: 40px;
        /* padding-left: 20px; */

        border-right: 2px solid rgba(100, 100, 100, 0.2);

        height: 919px;
    }
</style>