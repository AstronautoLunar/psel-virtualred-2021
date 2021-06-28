<template>
    <div class="DiplomasItemSideMenu"
        @click="$emit('click-navigation', `${textNavigation}`)"
    >
        <div class="area-icon">
            <img
                class="icon"
                :src="require(`../assets/${srcIcon}`)"
                :alt="altNameImg"
            />
        </div>
        <span 
            class="item-text"
            :style="styleSpan"    
        >
            {{ textItem }}
        </span>
    </div>
</template>

<script>
    export default {
        name: "DiplomasItemSideMenu",
        components: {

        },
        data() {
            return {
                styleSpan: ""
            }
        },
        props: {
            srcIcon: {
                type: String,
                required: true,
            },
            altNameImg: {
                type: String,
                required: true,
            },
            textItem: {
                type: String,
                required: true,
            },
            textNavigation: {
                type: String,
                required: true,
            },
            activeComponent: {
                type: Boolean,
                required: true,
            },
        },
        mounted() {
            if(this.activeComponent === true) {
                this.styleSpan = "color: black;"
            }
        },
        beforeUpdate() {
            if(this.activeComponent === true) {
                this.styleSpan = "color: black;"
            } else {
                this.styleSpan = "";
            }
        }
    }
</script>

<style scoped>
    div.DiplomasItemSideMenu {
        display: flex;
        align-items: center;

        cursor: pointer;
        
        margin-bottom: 40px;
    }

    div.area-icon {
        width: 60px;

        position: relative;
    }

    img.icon {

        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    span.item-text {
        color: var(--color-text-disabled);
    }
</style>