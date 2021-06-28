<template>
    <div class="DiplomasSearch">
        <img
            class="icon-search"    
            src="../assets/search-icon.svg"
            alt="icon search"
        />
        <input
            type="text"
            :value="valueName"
            v-on:change="$emit('change-input', '$event.target.value')"
            placeholder="Buscar Funcionalidade"
        />
    </div>
</template>

<script>
    export default {
        name: "DiplomasSearch",
        components: {

        },
        props: {
            valueName: {
                type: String,
                required: true,
            },
        },
    }
</script>

<style scoped>
    div.DiplomasSearch {
        width: 476px;
        height: 43px;
        background-color: var(--white); 

        padding: 10px;

        display: flex;
        align-items: center;

        box-sizing: border-box;

        border-radius: 10px;
    }

    img.icon-search {
        margin: 0 10px;
    }

    input[type="text"] {
        border: none;
        outline: none;

        width: 100%;
    }

    input[type="text"]::placeholder {
        color: var(--color-text-disabled);
    }
</style>