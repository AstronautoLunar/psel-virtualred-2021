<template>
    <header id="DiplomasHeader">
        <div id="area-search-logo">
            <img
                id="logo"
                src="../assets/ellipse-logo.svg"
                alt="logo diplomas"
            />
            <DiplomasSearch/>
        </div>
        <DiplomasAreaUser
            img-user="default-user.png"
            text-strong-user="Super Admin"
            text-normal-user="Super Admin"
        />
    </header>
</template>

<script>
    import DiplomasSearch from './DiplomasSearch.vue';
    import DiplomasAreaUser from './DiplomasAreaUser.vue';

    export default {
        name: "DiplomasHeader",
        components: {
            DiplomasSearch,
            DiplomasAreaUser,
        }
    }
</script>

<style scoped>
    header#DiplomasHeader {
        width: 100%;
        height: 101px;

        background-color: var(--main-header);

        justify-content: space-between;
    }

    header#DiplomasHeader, div#area-search-logo {
        display: flex;
        align-items: center;
    }

    img#logo {
        margin: 0 20px;
    }

    /* div#area-search-logo {
    } */
</style>