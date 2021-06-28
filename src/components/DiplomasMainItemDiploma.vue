<template>
    <div id="DiplomasMainItemDiploma">
        <h2>Templates de diplomas cadastrados</h2>
        <div id="area-diplomas-registered">
            <div id="filter-diplomas-registered">
                <div id="bar-filter">
                    <div
                        id="area-filter-text"
                    >
                        <img
                            id="icon-filter"
                            src="../assets/filterIcon.svg"
                            alt="Filter icon"
                        />
                        <span
                            class="text-filter"
                        >
                            Filtros
                        </span>
                    </div>
                    <div id="line">

                    </div>
                    <span 
                        class="text-filter"
                    >
                        Ordenar por
                    </span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "DiplomasMainItemDiploma",
        components: {

        },
    }
</script>

<style scoped>
    div#DiplomasMainItemDiploma {
        padding-left: 20px;
        
        box-sizing: border-box;
    }

    div#DiplomasMainItemDiploma,
    div#area-diplomas-registered,
    div#filter-diplomas-registered {
        width: 100%;
    }

    div#filter-diplomas-registered {
        justify-content: space-between;
    }

    div#bar-filter, 
    div#filter-diplomas-registered,
    div#area-filter-text {
        display: flex;
        align-items: center;
    }

    div#line {
        height: 25px;
        width: 1px;

        background-color: var(--color-lines-gray);

        margin: 0 20px;
    }
    
    img#icon-filter {
        margin: 0 5px;
    }

    span.text-filter {
        color: var(--color-text-disabled);
    }

</style>