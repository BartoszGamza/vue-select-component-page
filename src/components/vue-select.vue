<template>
  <div class="selector" @click="show = !show">
    <div class="selectorInner">
      {{selectedName}}
    </div>
    <div class="cardPopup">
      <div v-if="show" class="elements" v-for="option in options" :key="option.id" @click="selector(option)">
        <div class="cardPopupInner">
          {{option}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['selected', 'options'],
  data () {
    return {
      show: false
    }
  },
  methods: {
    selector (user) {
      this.selected = user
      this.$emit('selectedItem', user)
    }
  },
  computed: {
    selectedName () {
      const obj = this.options
      if (obj === undefined) {
        return 'placeholder'
      } else {
        return this.selected
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.selector {
  box-sizing: border-box;
  width: 100%;
  height: 30px;
  background-color: white;
  border-radius: 15px;
  text-align: left;
  vertical-align: middle;
  cursor: pointer;
  -webkit-box-shadow: 5px 10px 10px 0px rgba(0,0,0,0.16);
  -moz-box-shadow: 5px 10px 10px 0px rgba(0,0,0,0.16);
  box-shadow: 5px 10px 10px 0px rgba(0,0,0,0.16);

}
.selectorInner {
  display: inline-block;
  vertical-align: middle;
  margin-left: 25px;
  margin-top: 5px;
  text-align: left;
  color: gray;
  position: fixed;
}
.cardPopup {
  position: relative;
  left: 0;
  box-sizing: border-box;
  margin-left: auto;
  margin-right: auto;
  border-radius: 15px;
  color: gray;
  width: 100%;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  background-color: white;
  cursor: pointer;
}
.cardPopupInner {
  padding: 5px 0px 5px 0px;
  margin: 0px 25px 0px 25px;
}
</style>
