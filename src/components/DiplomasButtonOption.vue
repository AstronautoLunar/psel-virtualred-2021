<template>
    <div class="DiplomasButtonOption">
        <img
            :src="require(`../assets/${imgIconSrc}`)"
            :alt="altIconText"
        />
    </div>
</template>

<script>
    export default {
        name: "DiplomasButtonOption",
        components: {

        },
        props: {
            imgIconSrc: {
                type: String,
                required: true,
            },
            altIconText: {
                type: String,
                required: true,
            }
        }
    }
</script>

<style scoped>
    div.DiplomasButtonOption {
        width: 40px;
        height: 40px;

        background-color: var(--green);

        border-radius: 100%;

        display: flex;
        justify-content: center;
        align-items: center;

        margin-right: 20px;
    }

    div.DiplomasButtonOption:last-of-type {
        margin-right: 0px;
    }
</style>