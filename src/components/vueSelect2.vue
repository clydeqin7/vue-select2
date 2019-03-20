<template>
  <div class="select1" id="vueSelect2Wrapper">
    <select id="vueSelect2">
      <option v-for="item in options" :value="item[tagValue !== '' ? tagValue : label]">{{item[label]}}</option>
    </select>
  </div>
</template>

<script>

    export default {
      name: "vueSelect2",
      model: {
        prop: 'optionValue',
        event: 'change'
      },
      props: {
        optionValue: [String, Number],
        options: {
          type: Array,
          default: function() {
            return []
          },
          required: true,
        },
        label: [String, Number],
        tagValue: {
          type: [String, Number],
          default: ''
        },
      },
      data() {
        return {
          text: ''
        }
      },
      watch: {
        optionValue: function (newValue) {
          console.log('=select2=', newValue)
        }
      },
      created() {
        $(function(){
          $('#vueSelect2').select2({
            placeholder: '请选择桥梁',
            language: 'zh-CN'
          });
        });
      },
      mounted() {
        let _this = this
        $('#vueSelect2').on('change', function() {
          console.log($('#vueSelect2').children('option:selected').val(), '--------')
          _this.$emit('change', $('#vueSelect2').children('option:selected').val())
        })
      },
      methods: {
        // selectChange() {
        //   console.log($('#vueSelect2').children('option:selected').val(), '--------')
        //   this.$emit('change', $event.target.optionValue)
        //   // this.$emit('change', $('#vueSelect2').children('option:selected').val())
        // }
      }
    }
</script>

<style lang="scss" scoped>
.select1{
  width: 200px;
}
#vueSelect2{
  width: 200px;
}

</style>
<style lang="scss">
  #vueSelect2Wrapper {
    .select2-container--default .select2-selection--single .select2-selection__rendered {
      color: #606266;
    }
    .select2-results{
      ul.select2-results__options{
        li.select2-results__option{
          color: red !important;
        }
      }
    }
    :focus{
      outline-color: red !important;
    }
    .select2-container--default .select2-search--dropdown .select2-search__field:focus {
      outline-color: red !important;
    }
  }
</style>
