<!--  -->
<template>
  <div>
    <dropdown
    :title="dropdown"
    @onselect="onselect"
    :dropdownList="dropdownList">
    </dropdown>
    <div class="value">
      你选择的是
      {{value}}
    </div>
  </div>
</template>
<script>
import dropdown from '../components/dropDown'

export default {
  data () {
    return {
      dropdown: 'dropdown',
      value: '',
      dropdownList: [
        {
          name: 'apple',
          value: '001',
        },
        {
          name: 'pen',
          value: '002',
        },
        {
          name: 'pineapple',
          value: '003',
        },
        {
          name: 'banana',
          value: '004',
        },
      ],
    };
  },
  components: {
    dropdown,
  },
  mounted(){

  },
  methods: {
    onselect(value) {
      this.value = value
    }
  }
}

</script>
<style scoped>

</style>