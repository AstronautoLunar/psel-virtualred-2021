<template>
    <div class="DiplomasAreaUser">
        <img
            class="image-user"
            :src="require(`../assets/${imgUser}`)"
            alt="User image"
        />
        <div class="area-text-user">
            <span class="strong-text-user">
                {{ textStrongUser }}
            </span>
            <span class="normal-text-user">
                {{ textNormalUser.toUpperCase() }}
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "DiplomasAreaUser",
        components: {

        },
        props: {
            imgUser: {
                type: String,
                required: true,
            },
            textStrongUser: {
                type: String,
                required: true,
            },
            textNormalUser: {
                type: String,
                required: true,
            },
        }
    }
</script>

<style scoped>
    div.DiplomasAreaUser {
        display: flex;
        align-items: center;

        margin-right: 110px;
    }

    img.image-user {
        margin: 10px;

        width: 40px;
        height: 40px;

        border-radius: 10px;
    }

    div.area-text-user {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: flex-start;
    }

    span.strong-text-user {
        font-weight: bold;
        font-size: 16px;

        color: var(--text-main-black);
    }

    span.normal-text-user {
        color: var(--color-contrast-gray);

        font-size: 10px;
    }

</style>