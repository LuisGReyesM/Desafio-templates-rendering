<template>
  <div id="app">
    <form>
      <div>
        <label>Color de fondo:</label>
      </div>
      <div>
        <input type="text" name="colorFondo" v-model="tarjeta.colorFondo" />
      </div>

      <div>
        <label>Color Texto: </label>
      </div>
      <div>
        <input type="text" name="colorTexto" v-model="tarjeta.colorTexto" />
      </div>

      <div>
        <label>Mostrar texto: </label>
        <input type="checkbox" name="checkVisible" v-model="tarjeta.checkVisible" />
      </div>

      <div>
        <label>Borde: </label>
      </div>
      <div>
        <input type="range" v-model="tarjeta.borde" min="0" max="100" step="1" />
      </div>

      <div>
        <label>Contenido textual: </label>
      </div>
      <div>
        <textarea name="contenido" v-model="tarjeta.contenido" rows="2" cols="50"></textarea>
      </div>

      <div>
        <label>Tipografía: </label>
        <select name="tipografia" v-model="tarjeta.tipografia">
          <option v-for="opcion in opciones" :key="opcion" :value="opcion">
            {{ opcion }}
          </option>
        </select>
      </div>

      <div>
        <label>Opaco: </label>
        <input type="checkbox" name="checkOpaco" v-model="tarjeta.checkOpaco" />
      </div>

      <div>
        <label>Tamaño de letra</label>
        <ul>
          <li style="display: inline-block; margin-right: 10px;">
            <input type="radio" value="20" name="tamanoLetras" v-model="tarjeta.tamanoLetras" />
            Pequeño
          </li>
          <li style="display: inline-block; margin-right: 10px;">
            <input type="radio" value="25" name="tamanoLetras" v-model="tarjeta.tamanoLetras" />
            Mediano
          </li>
          <li style="display: inline-block; margin-right: 10px;">
            <input type="radio" value="40" name="tamanoLetras" v-model="tarjeta.tamanoLetras" />
            Grande
          </li>
        </ul>
      </div>
    </form>

    <div 
      class="figura" 
      :style="{
        background: tarjeta.colorFondo,
        color: tarjeta.colorTexto,      
        opacity: tarjeta.checkOpaco ? 0.5 : 1,
        fontFamily: tarjeta.tipografia,
        fontSize: tarjeta.tamanoLetras + 'px',
        borderRadius: tarjeta.borde + 'px'
      }"   

    >    
      <div v-if="tarjeta.checkVisible">
        {{ tarjeta.contenido }}
      </div>      
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      tarjeta: {
        colorFondo: "",
        colorTexto: "",
        checkVisible: false,
        borde: 0,
        contenido: "",
        tipografia: "",
        checkOpaco: false,
        tamanoLetras: "20",
      },
      opciones: ['Arial', 'Verdana', 'Courier', 'Times New Roman'],
    };
  },
};
</script>

<style>
* {
  margin: 0;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: sans-serif;
}

#app {
  display: flex;
  gap: 40px;
}

form {
  padding: 18px;
  box-shadow: 1px 1px 1px 1px gray; 
  display: flex;
  flex-direction: column;
  gap: 15px;
  justify-content: center;
  background-color: #255255;
  color: white;
  font-size: medium;
  margin-top: 80px;
}

.figura {
  width: 400px;
  height: 230px;
  color: white;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0px 0px 10px 2px black;
  display: flex;
  flex-direction: column;
  justify-content: center;   
  text-align: center;  
  margin-top: 180px;
}

input, select, textarea{
  font-family: "Cooper Black"; 
}
</style>
