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
                    <div 
                        class="button-option"
                    >
                        <img
                            src="../assets/starIcon.svg"
                            alt="Star icon"
                        />
                    </div>
                </div>
                <div class="option">
                    <span style="margin-right: 20px;">
                        Campos:
                    </span>
                    <div 
                        class="button-option"
                    >
                        <img
                            src="../assets/TIcon.svg"
                            alt="T icon"
                        />
                    </div>
                    <div 
                        class="button-option"
                        v-on:click="goInputImageIncrement"
                    >
                        <input
                            type="file"
                            @change="incrementImage"
                            ref="fileIncrement"
                            style="display: none;"
                        />
                        <img
                            src="../assets/photoIconOption.svg"
                            alt="photo icon"
                        />
                    </div>
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
            alignItems="flex-start"
        >
            <div id="manipulator-image">
                <canvas id="tela" ref="tela" width="800" height="500">

                </canvas>
                <div id="tools-manipulator-image">
                    <div id="coordenates-image">
                        <div class="column-coordenates">
                            <div class="coordenate">
                                <span class="type-value">
                                    X
                                </span>
                                <span class="value">
                                    {{
                                        currentScreen.x
                                    }}
                                </span>
                            </div>
                            <div class="coordenate">
                                <span class="type-value">
                                    W
                                </span>
                                <span class="value">
                                    {{ currentScreen.width }}
                                </span>
                            </div>
                        </div>
                        <div class="column-coordenates">
                            <div class="coordenate">
                                <span class="type-value">
                                    Y
                                </span>
                                <span class="value">
                                    {{
                                        currentScreen.y
                                    }}
                                </span>
                            </div>
                            <div class="coordenate">
                                <span class="type-value">
                                    H
                                </span>
                                <span class="value">
                                    {{ currentScreen.height }}
                                </span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </DiplomasAreaDiploma>
    </div>
</template>

<script>
    import DiplomasAreaDiploma from './DiplomasAreaDiploma.vue';

    export default {
        name: "DiplomasRegisterDiploma",
        components: {
            DiplomasAreaDiploma,
        },
        data() {
            return {
                screen: {
                    width: 300,
                    height: 300,
                },
                currentScreen: {
                    width: 0,
                    height: 0,
                    x: 0,
                    y: 0,
                },
                images: [

                ]
            }
        },
        methods: {
            goInput() {
                this.$refs.file.click();
            },
            getFile(file) {
                let url = URL.createObjectURL(file.target.files[0]);
                let tela = this.$refs.tela;
                let context = tela.getContext('2d');
                let img = new Image();
                img.src = url;
                let currentScreenOnLoad = this.currentScreen
                img.onload = function() {
                    tela.width = img.width;
                    tela.height = img.height
                    currentScreenOnLoad.width = img.width;
                    currentScreenOnLoad.height = img.height;
                    context.drawImage(
                            img, 
                            0, 
                            0, 
                            tela.width, 
                            tela.height
                    );
                }
            },
            goInputImageIncrement() {
                this.$refs.fileIncrement.click();
            },
            incrementImage(file) {
                let url = URL.createObjectURL(file.target.files[0]);
                let tela = this.$refs.tela;
                let context = tela.getContext('2d');
                console.log(context);
                let imgCreated = new Image();
                imgCreated.src = url;
                this.images = this.images.concat([ imgCreated ]);
                let imagesArray = this.images
                console.log(imagesArray);
                function run() {
                    for(let i = 0; i < imagesArray.length; i++) {
                        context.drawImage(
                            imagesArray[i], 
                            0, 
                            0, 
                            tela.width, 
                            tela.height, 
                            50, 
                            50, 
                            tela.width / 2, 
                            tela.height / 2,
                        );
                    }
                    window.requestAnimationFrame(run);
                }
                
                run();
                
                // imagesArray[0].addEventListener('mousedown', event => {
                //     this.images[0].onload = function() {


                //         context.drawImage(
                //             imgCreated, 
                //             event.layerX, 
                //             event.layerY, 
                //             tela.width, 
                //             tela.height, 
                //             50, 
                //             50, 
                //             tela.width/2, 
                //             tela.height/2
                //         );
                //     }
                // })
                
            }
        },
        mounted() {
            let tela = this.$refs.tela;

            let currentScreenValue = this.currentScreen

            tela.addEventListener('mousemove', event => {
                currentScreenValue.x = event.layerX
                currentScreenValue.y = event.layerY
            });
        }
    }

</script>

<style scoped>

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
    div#buttons-option-document,
    div#manipulator-image,
    div#coordenates-image,
    div.row-coordenates,
    div#tools-manipulator-image,
    div.coordenate {
        display: flex;
    }

    div#button-uploud-image, 
    div.option,
    div#buttons-option-document,
    div.row-coordenates,
    div#tools-manipulator-image {
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

    div.button-option {
        width: 40px;
        height: 40px;

        background-color: var(--green);

        border-radius: 100%;

        display: flex;
        justify-content: center;
        align-items: center;

        margin-right: 20px;

        cursor: pointer;
    }

    div.button-option:last-of-type {
        margin-right: 0px;
    }

    div#buttons-option-document {
        justify-content: center;
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

    div#manipulator-image {
        width: 100%;

        display: flex;

        padding-top: 20px;
        
        box-sizing: border-box;
    }

    div#tools-manipulator-image {
        flex-direction: column;
    }

    div#tools-manipulator-image {
        width: 350px;
        height: 100vh;

    }

    div#coordenates-image {
        background-color: var(--white);

        box-shadow: 1px 2px 5px 0.1px rgba(20, 20, 20, 0.5);

        width: 182px;
        height: 80px;
        
        margin-top: 25px;
        
        padding: 10px;
    }

    div.column-coordenates {
        width: 50%;
        height: 100%;

        margin-top: 10px;
    }

    /* div.coordenate {
        margin-right: 50px;
    } */

    div.coordenate:last-of-type {
        margin-top: 20px;
    }

    span.type-value {
        margin: 0 10px;

        color: var(--color-text-disabled)
    }

    canvas#tela {
        background-color: black;
    }
</style>
