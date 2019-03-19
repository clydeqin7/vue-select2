<template>
  <div class="select1">
    <select id="vueSelect2" @change="selectChange">
      <option v-for="item in options" :value="item[value !== '' ? value : label]">{{item[label]}}</option>
    </select>
  </div>
</template>

<script>
    $(function(){
      $('#vueSelect2').select2({
        language: 'zh-CN'
      });
    });
    export default {
      name: "vueSelect2",
      model: {
        prop: 'optionValue',
        event: 'change'
      },
      props: {
        optionValue: String,
        options: {
          type: Array,
          default: function() {
            return []
          },
          required: true,
        },
        label: [String, Number],
        value: {
          type: [String, Number],
          default: ''
        }

      },
      data() {
        return {
          text: ''
        }
      },
      mounted() {
        // $('#vueSelect2').on('change', function() {
        //   console.log($('#vueSelect2').children('option:selected').val(), '--------')
        // })
      },
      methods: {
        selectChange() {
          this.$emit('change', $event.target.optionValue)
        }
      }
    }
</script>

<style scoped>
.select1{
  width: 200px;
}
#vueSelect2{
  width: 200px;
}
</style>
