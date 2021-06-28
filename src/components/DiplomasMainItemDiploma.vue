<template>
    <div id="DiplomasMainItemDiploma">
        <div id="area-filter-options">
            <div
                id="filter-diplomas-registered"
            >
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
            <div id="filter-buttons">
                <div 
                    class="buttons"
                    v-on:click="byData"
                >
                    <span>
                        Data
                    </span>
                </div>
                <div 
                    class="buttons"
                    v-on:click="byName"
                >
                    <span>
                        Nome
                    </span>
                </div>
                <div 
                    class="buttons"
                >
                    <span>
                        Atualização
                    </span>
                </div>
            </div>
        </div>
        <div id="area-diplomas-registered">
            <div id="message-diplomas-registered">
                <span>
                    Diplomas
                </span>
            </div>
            <DiplomasItemTemplate
                v-for="diploma in diplomas"
                :key="diploma.id"
                :title-name="diploma.titleName"
                :text-school="diploma.textSchool"
                :text-course="diploma.textCourse"
                :number-users="diploma.numberUsers"
                :color-one="diploma.colorOne"
                :color-two="diploma.colorTwo"
            />
        </div>
    </div>
</template>

<script>
    import DiplomasItemTemplate from './DiplomasItemTemplate.vue';

    export default {
        name: "DiplomasMainItemDiploma",
        components: {
            DiplomasItemTemplate,
        },
        data() {
            return {
                diplomas: [],
            }
        },
        methods: {
            byName() {
                let diplomasNew = this.diplomas.sort(function (a, b) {
                    if(a.titleName < b.titleName) {
                        return -1;
                    } else if(a.titleName > b.titleName) {
                        return 1;
                    }
                });
                console.log(diplomasNew);
                this.diplomas = diplomasNew;
            },
            byData() {
                let diplomasNew = this.diplomas.sort(function (a, b) {
                    if(a.id < b.id) {
                        return -1;
                    } else if(a.id > b.id) {
                        return 1;
                    }
                });
                console.log(diplomasNew);
                this.diplomas = diplomasNew;
            },
        },
        created() {
            this.diplomas = [
                {
                    id: 1,
                    titleName: "B Título do diploma",
                    textSchool: "Escola associada",
                    textCourse: "Curso associado",
                    numberUsers: 12,
                    colorOne: "blue",
                    colorTwo: "red",
                },
                {
                    id: 2,
                    titleName: "A Título do diploma",
                    textSchool: "Escola associada",
                    textCourse: "Curso associado",
                    numberUsers: 12,
                    colorOne: "yellow",
                    colorTwo: "green",
                },
                {
                    id: 3,
                    titleName: "C Título do diploma",
                    textSchool: "Escola associada",
                    textCourse: "Curso associado",
                    numberUsers: 12,
                    colorOne: "purple",
                    colorTwo: "blue",
                },
            ]
        }
    }
</script>

<style scoped>
    div#DiplomasMainItemDiploma {
        box-sizing: border-box;

        position: relative;
    }

    div#DiplomasMainItemDiploma,
    div#area-filter-options,
    div#filter-diplomas-registered,
    div#area-diplomas-registered {
        width: 100%;
    }

    div#filter-diplomas-registered {
        justify-content: space-between;
    }

    div#bar-filter, 
    div#filter-diplomas-registered,
    div#area-filter-text,
    div#area-filter-options,
    div.buttons,
    div#area-diplomas-registered,
    div#button-register-diploma {
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

    div#filter-buttons {
        display: flex;
        align-items: center;

        margin-right: 20px;
    }

    div.buttons {
        width: 100px;
        height: 40px;

        background-color: var(--main-header);

        justify-content: center;

        margin: 0 1px;

        transition: all 0.2s;

        cursor: pointer;
    }

    div.buttons > span {
        color: white;
    }

    div.buttons:first-of-type {
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
    }

    div.buttons:last-of-type {
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
    }

    div.buttons:hover {
        background-color: var(--text-main-black);
    }

    div#area-diplomas-registered {
        flex-direction: column;
        justify-content: flex-start;

        border-top: 2px dashed var(--color-lines-gray);

        position: relative;

        margin-top: 30px;

        height: 500px;

        padding-top: 25px;
        box-sizing: border-box;
    }

    div#message-diplomas-registered {
        width: 64px;
        height: 20px;

        background-color: var(--text-main-black);

        display: flex;
        justify-content: center;
        align-items: center;

        position: absolute;
        top: -2.2%;
        left: 15px;

        border-radius: 20px;
    }

    div#message-diplomas-registered > span {
        color: var(--white);

        font-size: 10px;
    }
</style>