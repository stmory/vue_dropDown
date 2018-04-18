<!--  -->
<template>
  <div class="dr_main"  @click="click">
    <div class="dropDown_main">
      <div class="dropDown_title">
        {{title}}
      </div>
      <svg :class="svg" width="12" height="7" version="1.1" xmlns="http://www.w3.org/2000/svg">
        <polygon points="6,0 12,7 0,7" style="fill:#ffffff"/>
      </svg>
    </div>
    <transition name="fade">
      <dropdownlist 
        :dropdownList="dropdownList"
        @setvalue="setvalue"
        v-show="show">
      </dropdownlist>
    </transition>
  </div>
</template>

<script>
import dropdownlist from './dropDownList'

export default {
  data () {
    return {
      show: false,
      svg: 'svg1',
      select: {
        value: '',
        name: '',
      },
    };
  },
  props: {
    title: String,
    dropdownList: Array,
  },
  mounted() {
    document.onclick = function(event) {
      event.srcElement.className !== 'dr_main'
      this.show = false
    }
  },
  components: {
    dropdownlist,
  },
  methods: {
    click() {
      this.show = !this.show
      this.svg = this.svg === 'svg1' ? 'svg2' : 'svg1'
    },
    setvalue(name, value) {
      this.select.value = value
      this.select.name = name
      this.$emit('onselect', this.select)
    },
  },
}

</script>
<style scoped>
.dr_main{
  position: relative;
}
.dropDown_main{
  width: 200px;
  height: 40px;
  line-height: 40px;
  position: relative;
  color: #ffffff;
  border-radius: 6px;
  cursor: pointer;
  transition: all .5s;
  background-color: rgb(107, 151, 231);
  z-index: 100;
}
.dropDown_title{
  width: 100px;
  overflow: hidden;
  margin: 0 auto;
}
.dropDown_main .svg1{
  position: absolute;
  transition: all .3s;
  top: 16px;
  right: 36px;
  transform: rotate(-180deg)
}
.dropDown_main .svg2{
  position: absolute;
  transition: all .3s;
  top: 16px;
  right: 36px;
  transform: rotate(0deg)
}
.dropDown_main:hover{
  background-color: rgb(127, 164, 233);
}
.fade-enter-active, .fade-leave-active {
  transition: all .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
  transform: translateY(-40%) scaleY(0.5);
}
</style>