<template>
    <div class="mx-2">
        <select v-model="selected" v-on:click="setParentSelectedCategory" class="form-select" aria-label="Default select example">
            <option disabled value="">Category</option>
            <option value="Tesla">Tesla</option>
            <option value="Porsche">Porsche</option>
            <option value="Toyota">Toyota</option>
            <option value="Honda">Honda</option>
            <option value="Mazda">Mazda</option>
            <option value="Mercedes-Benz">Mercedes-Benz</option>
            <option value="Lexus">Lexus</option>
            <option value="Lamborghini">Lamborghini</option>
            <option value="Audi">Audi</option>
            <option value="BMW">BMW</option>
        </select>
    </div>
</template>

<script>
export default {
  name: 'selectCategory',
  data(){
      return {
          selected: ""
      }
  },
  methods:{
      setParentSelectedCategory:function(){
          this.$emit('select-category',this.selected);
      }
  }

}
</script>