<template>
    <div id="DiplomasRegisterDiploma">
        <div id="option-register">
            <div id="button-uploud-image">
                <span id="text-uploud-image">
                    Subir imagem
                </span>
                <img
                    src="../assets/photoIcon.svg"
                    alt="icon uploud image"
                />
            </div>
            <div class="option">
                <span>
                    formas:
                </span>
                <div class="button-option">
                    <img
                        src="../assets/starIcon.svg"
                        alt="icon star"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "DiplomasRegisterDiploma",
        components: {

        },
    }
</script>

<style scoped>
    div#DiplomasRegisterDiploma {
        box-sizing: border-box;

        padding: 10px;
    }

    div#option-register {
        width: 100%;

        display: flex;
        justify-content: space-around;
        align-items: center;
    }

    div#button-uploud-image {
        width: 200px;
        height: 40px;

        background-color: var(--text-main-black);

        justify-content: space-around;

        border-radius: 10px;
    }

    div#button-uploud-image, 
    div.option,
    div.option > div.button-option {
        display: flex;
        align-items: center;
    }


    span#text-uploud-image {
        color: var(--white);
    }

    div.option {
        border-left: 1px solid var(--color-lines-gray);
    }

    div.option > span {
        color: var(--color-text-disabled);

        margin: 0 35px;
    }

    div.option > div.button-option {
        width: 40px;
        height: 40px;

        background-color: var(--green);

        border-radius: 100%;

        justify-content: center;
    }
</style>
