<template>
  <main id="main">
    <DiplomasHeader/>
    <div id="area-sidemenu-and-main">
      <DiplomasSideMenu>
        <template #items>
          <div class="area-sideMenu">
            <DiplomasItemSideMenu
              @click-navigation="clickNavigation"
              src-icon="inicioIcon.svg"
              alt-name-img="Icon inicio"
              text-item="Inicio"
              text-navigation="inicio"
              :active-component="inicio"
            />
            <DiplomasItemSideMenu
              @click-navigation="clickNavigation"
              src-icon="escolaIcon.svg"
              alt-name-img="Icon escolas"
              text-item="Escolas"
              text-navigation="escola"
              :active-component="escola"
            />
            <DiplomasItemSideMenu
              @click-navigation="clickNavigation"
              src-icon="usuarioIcon.svg"
              alt-name-img="Icon usuarios"
              text-item="Usuários"
              text-navigation="usuario"
              :active-component="usuario"
            />
            <DiplomasItemSideMenu
              @click-navigation="clickNavigation"
              src-icon="diplomasIcon.svg"
              alt-name-img="Icon diplomas"
              text-item="Diplomas"
              text-navigation="diplomas"
              :active-component="diplomas"
            />
          </div>
        </template>
      </DiplomasSideMenu>
      <keep-alive>
        <component :is="currentComponent">

        </component>
      </keep-alive>
    </div>
  </main>
</template>

<script>
  import DiplomasHeader from './components/DiplomasHeader';
  import DiplomasSideMenu from './components/DiplomasSideMenu.vue';
  import DiplomasItemSideMenu from './components/DiplomasItemSideMenu.vue';
  import DiplomasMainItemDiploma from './components/DiplomasMainItemDiploma.vue';

  import { defineAsyncComponent } from 'vue';

  export default {
    name: 'App',
    components: {
      DiplomasHeader,
      DiplomasSideMenu,
      DiplomasItemSideMenu,
      DiplomasMainItemDiploma,
      DiplomasMainItemInicio: defineAsyncComponent(() => import('./components/DiplomasMainItemInicio.vue')),
      DiplomasMainItemUsuario: defineAsyncComponent(() => import('./components/DiplomasMainItemUsuario.vue')),
      DiplomasMainItemEscolas: defineAsyncComponent(() => import('./components/DiplomasMainItemEscolas.vue')),
    },
    data() {
      return {
        currentComponent: "DiplomasMainItemDiploma",
        inicio: false,
        escola: false,
        usuario: false,
        diplomas: true,
      }
    },
    methods: {
      clickNavigation(value) {
        let valueArray = value.split(' ');

        switch(valueArray[0]) {
          case "inicio":
            this.currentComponent = "DiplomasMainItemInicio";
            this.inicio = true;
            this.escola = false;
            this.usuario = false;
            this.diplomas = false;

            break;
          case "escola":
            this.currentComponent = "DiplomasMainItemEscolas";
            this.inicio = false;
            this.escola = true;
            this.usuario = false;
            this.diplomas = false;

            break;
          case "usuario":
            this.currentComponent = "DiplomasMainItemUsuario";
            this.inicio = false;
            this.escola = false;
            this.usuario = true;
            this.diplomas = false;
          
            break;
          case "diplomas":
            default:
              this.currentComponent = "DiplomasMainItemDiploma";
              this.inicio = false;
              this.escola = false;
              this.usuario = false;
              this.diplomas = true;

            break;
        } 
      }
    }
  }
</script>

<style>
  body {
    margin: 0;
    padding: 0;

    font-family: Rubik;
  }

  /* main#main {
  } */

  :root {
    --main-header: #B28DD6;
    --text-main-black: #000000;
    --color-lines-gray: #C4C4C4;
    --color-contrast-gray: #F9F9F9;
    --color-text-disabled: #989898;
    --white: #FFFFFF;
  }

  div#area-sidemenu-and-main {
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
  }

  /* div#icon-area-sideMenu {

  } */

  div.area-sideMenu {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  img.image-icon-sideMenu {
    margin: 20px 0;
  }

</style>
