<template>
    <div id="DiplomasRegisterDiploma">
        <div id="area-option-register">
            <div id="option-register">
                <div id="button-uploud-image">
                    <!-- <span 
                        id="text-uploud-image"

                    >
                        Subir imagem
                    </span> -->
                    <input
                        type="file"
                        @change="pegarArquivo"
                        ref="file"
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
        <DiplomasAreaDiploma>
            <canvas id="tela" ref="tela">

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
                // data: []
            }
        },
        methods: {
            pegarArquivo(input) {
                console.log(input.target.files)
                // if (input.files && input.files[0]) {
                var reader = new FileReader();

                let image = new Image();
                console.log(this.$refs.tela);
                reader.onload = function (e) {
                    image.src = e.target.result;
                    console.log(e.target.result);
                };

                // console.log(image.width);
                // console.log(image.height);
                this.$refs.tela.width = image.width;
                this.$refs.tela.height = image.height;
                let context = this.$refs.tela.getContext('2d');

                context.drawImage(image, 0, 0, this.$refs.tela.width, this.$refs.tela.height);
                reader.readAsDataURL(input.target.files[0]);
                // }
               
            
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
