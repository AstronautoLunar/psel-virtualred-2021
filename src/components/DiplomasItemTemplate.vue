<template>
    <div class="DiplomasItemTemplate">
        <span class="title-item">
            {{ titleName }}
        </span>
        <span class="text-school-item">
            {{ textSchool }}
        </span>
        <span class="text-course-item">
            {{ textCourse }}
        </span>
        <span class="text-number-users">
            {{ numberUsers }} Usuários associados
        </span>
        <div class="colors">
            <div 
                class="colorOne"
                :style="colorOneDiv"
            >

            </div>
            <div 
                class="colorTwo"
                :style="colorTwoDiv"    
            >

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "DiplomasItemTemplate",
        components: {

        },
        props: {
            titleName: {
                type: String,
                required: true,
            },
            textSchool: {
                type: String,
                required: true,
            },
            textCourse: {
                type: String,
                required: true,
            },
            numberUsers: {
                type: Number,
                required: true,
            },
            colorOne: {
                type: String,
                required: true,
            },
            colorTwo: {
                type: String,
                required: true,
            },
        },
        data() {
            return {
                colorOneDiv: "",
                colorTwoDiv: "",
            }
        },
        created() {
            this.colorOneDiv = `background-color: ${this.colorOne};`;
            this.colorTwoDiv = `background-color: ${this.colorTwo};`;
        }
    }
</script>

<style scoped>
    div.DiplomasItemTemplate {
        width: calc(100% - 20px);
        height: 80px;

        display: flex;
        justify-content: space-around;
        align-items: center;

        background-color: var(--color-contrast-gray);

        border-radius: 10px;

        box-shadow: 3px 2px 5px 1px rgb(50, 50, 50, 0.5);
    }

    span.title-item {
        font-weight: bold;
    }

    div.colors {
        display: flex;
        justify-content: space-around;
        align-items: center;
    }

    div.colors > div {
        width: 40px;
        height: 40px;

        margin: 0 10px;

        border-radius: 100%;
    }
</style>