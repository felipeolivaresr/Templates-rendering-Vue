<script>
export default {
  data() {
    return {
      bgColor: 'darkgreen',
      textColor: 'white',
      showText: true,
      borderRadius: 0,
      textContent: '',
      fonts: ['sans-serif', 'serif', 'cursive', 'monospace'],
      opacity: false,
      fontSize: 'medium',
    }
  },
}
</script>

<template>
  <div class="container row">

    <div class="col-6 config-panel">
      <label>Color de fondo</label>
      <input type="text" v-model="bgColor" placeholder="darkgreen" />

      <label>Color de texto</label>
      <input type="text" v-model="textColor" placeholder="white" />

      <label>Mostrar texto</label>
      <input type="checkbox" v-model="showText" />

      <label>Borde</label>
      <input type="range" v-model="borderRadius" min="0" max="50" />

      <label>Contenido textual</label>
      <textarea v-model="textContent"></textarea>

      <select v-model="fontStyle">
        <option v-for="(font, index) in fonts" :key="index" :value="font">{{ font }}</option>
      </select>

      <label>Opaco</label>
      <input type="checkbox" v-model="opacity" />

      <label>Tamaño de letra</label>
      <div>
        <input type="radio" value="small" v-model="fontSize" /> Pequeño
        <input type="radio" value="medium" v-model="fontSize" /> Mediano
        <input type="radio" value="large" v-model="fontSize" /> Grande
      </div>
    </div>


    <div class="col-6">
      <div class="preview-panel"
        :style="{ backgroundColor: bgColor, color: textColor, borderRadius: borderRadius + '%', fontFamily: fontStyle }"
        :class="{
          'opacity-class': opacity,
          'font-small': fontSize === 'small',
          'font-medium': fontSize === 'medium',
          'font-large': fontSize === 'large'
        }">
        <p v-if="showText">{{ textContent }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.config-panel {
  background-color: #2f4f4f;
  padding: 20px;
  width: 300px;
  color: white;
  margin-right: 20px;
}


.preview-panel {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 300px;
  height: 300px;
  background-color: lightgreen;
  border-radius: 10px;
}


.font-small {
  font-size: 10px;
}

.font-medium {
  font-size: 25px;
}

.font-large {
  font-size: 55px;
}


.opacity-class {
  opacity: 0.5;
}


input,
select,
textarea {
  display: block;
  margin-bottom: 10px;
  width: 100%;
}

label {
  margin-bottom: 5px;
  display: block;
}

textarea {
  height: 50px;
}

input[type="checkbox"],
input[type="radio"] {
  display: inline;
  margin-right: 5px;
}
</style>