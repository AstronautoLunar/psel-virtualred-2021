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
      <div id="area-current-component">
        <div 
          id="registered-diploma"
          v-if="buttonRegisterDiploma"  
        >
          <h2
            v-if="register"
          >Templates de diplomas cadastrados</h2>
          <h2
            v-if="saveDiploma"
          >
            Cadastrar novo template
          </h2>
          <div
            class="button-diploma"
            v-if="register" 
            v-on:click="registerTemplate"  
          >
              <span>
                  Cadastrar
              </span>
          </div>
          <div
            class="button-diploma"
            v-if="saveDiploma"
          >
            <span>
              Salvar
            </span>
          </div>
        </div>
        <keep-alive>
          <component :is="currentComponent">

          </component>
        </keep-alive>
      </div>
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
      DiplomasRegisterDiploma: defineAsyncComponent(() => import('./components/DiplomasRegisterDiploma.vue')),
    },
    data() {
      return {
        currentComponent: "DiplomasMainItemDiploma",
        inicio: false,
        escola: false,
        usuario: false,
        diplomas: true,
        buttonRegisterDiploma: true,
        register: true,
        saveDiploma: false,
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
            this.buttonRegisterDiploma = false;
            this.register = true;
            this.saveDiploma = false;

            break;
          case "escola":
            this.currentComponent = "DiplomasMainItemEscolas";
            this.inicio = false;
            this.escola = true;
            this.usuario = false;
            this.diplomas = false;
            this.buttonRegisterDiploma = false;
            this.register = true;
            this.saveDiploma = false;

            break;
          case "usuario":
            this.currentComponent = "DiplomasMainItemUsuario";
            this.inicio = false;
            this.escola = false;
            this.usuario = true;
            this.diplomas = false;
            this.buttonRegisterDiploma = false;
            this.register = true;
            this.saveDiploma = false;
          
            break;
          case "diplomas":
            default:
              this.currentComponent = "DiplomasMainItemDiploma";
              this.inicio = false;
              this.escola = false;
              this.usuario = false;
              this.diplomas = true;
              this.buttonRegisterDiploma = true;
              this.register = true;
              this.saveDiploma = false;

            break;
        } 
      },
      registerTemplate() {
        this.currentComponent = "DiplomasRegisterDiploma";
        this.inicio = false;
        this.escola = false;
        this.usuario = false;
        this.diplomas = false;
        this.buttonRegisterDiploma = true;
        this.register = false;
        this.saveDiploma = true;
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
    --green: #68A35D;
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

  div#area-current-component {
    width: 100%;

    position: relative;
  }
  
  div.button-diploma {
    width: 100px;
    height: 40px;

    background-color: var(--text-main-black);

    position: absolute;
    right: 15px;
    top: 10px;

    display: flex;
    justify-content: center;
    align-items: center;

    border-radius: 10px;

    cursor: pointer;
  }

  div.button-diploma > span {
    color: var(--white);
  }
</style>
