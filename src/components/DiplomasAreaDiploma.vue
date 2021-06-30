<template>
    <div 
        class="DiplomasAreaDiploma"
        :style="style"    
    >
        <div id="message-diplomas-registered">
            <span>
                Diplomas
            </span>
        </div>
        <slot>

        </slot>
    </div>
</template>

<script>
    export default {
        name: "DiplomasAreaDiploma",
        components: {

        },
        data() {
            return {
                style: `flex-direction: ${this.flexDirection}; align-items: ${this.alignItems};`
            }
        },
        props: {
            flexDirection: {
                type: String,
                required: false,
            },
            alignItems: {
                type: String,
                required: false,
            }
        }
    }
</script>

<style scoped>
    div.DiplomasAreaDiploma {
        width: 100%;

        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;

        border-top: 2px dashed var(--color-lines-gray);

        position: relative;

        margin-top: 30px;

        height: 1000px;

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
        top: -1.2%;
        left: 15px;

        border-radius: 20px;
    }

    div#message-diplomas-registered > span {
        color: var(--white);

        font-size: 10px;
    }
</style>