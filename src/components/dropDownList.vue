<!--  -->
<template>
  <div class="dropDownList">
    <li class="li" v-for="(item, index) in dropdownList" :key="index" @click="click(item.name, item.value)">{{item.name}}</li>
  </div>
</template>

<script>
export default {
  data () {
    return {
    };
  },
  props: {
    dropdownList: Array,
  },
  methods: {
    click(name, value) {
      this.$emit('setvalue', name, value)
    },
  },
}

</script>
<style scoped>
.dropDownList{
  position: absolute;
  top: 46px;
  border-radius: 4px;
  left: 0;
  color: #666;
  width: 200px;
  padding: 10px 0;
  box-shadow: 0 1px 6px rgba(0,0,0,.2)
}
.dropDownList .li{
  height: 40px;
  line-height: 40px;
  list-style-type:none; 
  cursor: pointer;
  transition: all .3s;
}
.li:hover {
  background-color: #efefef;
}
</style>