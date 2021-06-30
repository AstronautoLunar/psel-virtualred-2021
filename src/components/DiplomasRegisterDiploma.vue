<template>
    <div id="DiplomasRegisterDiploma">
        <div id="area-option-register">
            <div id="option-register">
                <div id="button-uploud-image"
                    v-on:click="goInput"
                >
                    <span 
                        id="text-uploud-image"

                    >
                        Subir imagem
                    </span>
                    <input
                        type="file"
                        @change="getFile"
                        ref="file"
                        style="display: none;"
                    />

                    <img
                        src="../assets/photoIcon.svg"
                        alt="icon uploud image"
                    />
                </div>
                <div class="option">
                    <span>
                        formas:
                    </span>
                    <DiplomasButtonOption
                        imgIconSrc="starIcon.svg"
                        altIconText="Star icon"
                    />
                </div>
                <div class="option">
                    <span style="margin-right: 20px;">
                        Campos:
                    </span>
                    <DiplomasButtonOption
                        imgIconSrc="TIcon.svg"
                        altIconText="T icon"
                    />
                    <DiplomasButtonOption
                        imgIconSrc="photoIconOption.svg"
                        altIconText="photo icon"
                    />
                </div>
                <div class="option">
                    <span style="margin-right: 10px;">
                        Editando:
                    </span>
                    <div id="buttons-option-document">
                        <div class="button-document">
                            <span>Frente</span>
                        </div>
                        <div class="button-document">
                            <span>Verso</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <DiplomasAreaDiploma
            flexDirection="row"
        >
            <canvas id="tela" ref="tela" width="800" height="600">

            </canvas>
        </DiplomasAreaDiploma>
    </div>
</template>

<script>
    import DiplomasButtonOption from './DiplomasButtonOption.vue';
    import DiplomasAreaDiploma from './DiplomasAreaDiploma.vue';

    export default {
        name: "DiplomasRegisterDiploma",
        components: {
            DiplomasButtonOption,
            DiplomasAreaDiploma,
        },
        data() {
            return {
                tela: {
                    width: 300,
                    height: 300,
                }
            }
        },
        methods: {
            goInput() {
                this.$refs.file.click();
            },
            getFile(file) {
                let url = URL.createObjectURL(file.target.files[0]);
                let context = this.$refs.tela.getContext('2d');
                let img = new Image();
                img.src = url;
                let tela = this.$refs.tela;
                img.onload = function() {
                    tela.width = img.width;
                    tela.height = img.height
                    context.drawImage(img, 0, 0, tela.width, tela.height);
                }
            }
        }
    }

</script>

<style scoped>
    /* div#area-option-register {
        
    } */

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
    div.option {
        display: flex;
        align-items: center;
    }


    span#text-uploud-image {
        color: var(--white);

        cursor: pointer;
    }

    div.option {
        border-left: 1px solid var(--color-lines-gray);
    }

    div.option > span {
        color: var(--color-text-disabled);

        margin: 0 35px;
    }

    div#buttons-option-document {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    div.button-document {
        width: 100px;
        height: 40px;

        background-color: var(--main-header);

        display: flex;
        justify-content: center;
        align-items: center;

        margin-left: 2.5px;

        transition: all 0.2s;

        cursor: pointer;
    }

    div.button-document:first-of-type {
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
    }

    div.button-document:last-of-type {
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
    }

    div.button-document:hover {
        background-color: var(--text-main-black);
    }

    div.button-document > span {
        color: var(--white);

        font-size: 15px;
    }
</style>
