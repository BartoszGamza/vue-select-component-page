<template>
  <div id="app">
    <div class="header"></div>
    <div class="grid">
      <h1>Vue Select Component</h1>
      <p>Simple Vue selector component created with ❤️ by Bartosz Gamza</p>
      <div class="selectorWrapper">
        <vue-select
        :selected="selected"
        :options="options"
        v-on:selectedItem="changedSelect($event)"
        >
        </vue-select>
      </div>
      <div class="selected">
        Selected: {{selected}}
      </div>
    </div>
  </div>
</template>

<script>
import VueSelect from './components/vue-select'
export default {
  name: 'App',
  data () {
    return {
      selected: 'Pick something...',
      options: ['option1', 'option2', 'option3']
    }
  },
  methods: {
    changedSelect (item) {
      this.selected = item
    }
  },
  components: {
    VueSelect
  }
}
</script>

<style lang="scss" scoped>
body {
  padding: 0;
}
.header {
  width: 100%;
  height: 100%;
  background: linear-gradient(#00416A,#E4E5E6) ;
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
}
.grid {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  color: white;
  text-align: center;
}
.card {
  box-sizing: border-box;
  z-index: 2;
  margin-left:  auto;
  margin-right: auto;
  margin-top: 25px;
  margin-bottom: 25px;
  max-width: 800px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  background-color: white;
  border-radius: 5px;
  padding: 20px 40px 5px 40px;
}
.selectorWrapper {
  margin: 0 auto;
  max-width: 400px;
}
.selected {
  text-align: center;
  padding: 10px
}
</style>
