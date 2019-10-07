
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <div id="hello" v-on:click="press">{{ helloworld }}</div>
    <div v-if="seen">Boleano</div>
    <ul>
      <li v-for="todo in todos" v-bind:key="todo.text">{{todo.text}}</li>
    </ul>
    <input type="text" v-model="helloworld" />
    <custom_button
      nombre_bb="Eduardo"
      :function_click="change_red_style(blue_style)"
      color="red_style"
    />
    <custom_button
      nombre_bb="Eduardo"
      :function_click="change_red_style(red_style)"
      color="blue_style"
    />
    <p>HTML desde propiedades</p>
    <h1 v-html="html_example" :class="font_color"></h1>
    <h1 :class="font_color">{{html_example}}</h1>
    <h1 :class="{verdadero:object_classes.verdadero,falso:object_classes.falso}">Classes Example</h1>
    <h1 :class="object_classes">Object classes</h1>
    <h1 :class="[object_classes.clase_desde_objeto]">Object classes</h1>
    <h1 :style="object_style">Object style</h1>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import custom_button from "./components/custom_button.vue";

// ? @click === v-on:click
// ? :style === v-bind:style

export default {
  name: "app",
  data: function() {
    return {
      object_style: {
        color: "red",
        fontSize: "10rem"
      }, 
      red_style: "red",
      blue_style: "blue",
      font_color: "black",
      helloworld: "Hola mundo",
      seen: true,
      html_example: "<h1 style='color:red'>Hola mundo</h1>",
      todos: [
        { text: "Learn JavaScript" },
        { text: "Learn Vue" },
        { text: "Build something awesome" }
      ],
      object_classes: {
        verdadero: true,
        falso: true,
        clase_desde_objeto: "objeto"
      }
    };
  },
  created: function() {
    console.log("====================================");
    console.log(this);
    console.log("====================================");
  },
  //* it also exist updated & mounted & destroyec
  components: {
    HelloWorld,
    custom_button
  },
  computed: {
    // * method that are saved in cache so it's more quick to render than methods but is more recomended for static method or not dinamic
  },
  watch: {
    helloworld: function(oldHelloWorld, newHelloWorld) {
      console.log("====================================");
      console.log(newHelloWorld, oldHelloWorld);
      console.log("====================================");
    }
  },
  methods: {
    press: function() {
      this.helloworld = "Good bye";
    },
    change_red_style: function(color) {
      return () => {
        console.log("====================================");
        console.log(color);
        console.log("====================================");
        switch (color) {
          case "red":
            this.font_color = this.red_style;
            break;
          case "blue":
            this.font_color = this.blue_style;
            break;
          default:
            break;
        }
      };
    }
  }
};
</script>

<style>
.objeto {
  background: green;
}
.verdadero {
  background: yellow;
}
.falso {
  background: grey;
}
.blue {
  color: blue;
}
.black {
  color: black;
}
.red {
  color: red;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
