<template>
  <form class="well" @submit="formSubmit">
    <textarea class="form-control" rows="3" v-model="textToTranslate" placeholder="Enter a Word..."></textarea>
    <select class="form-control" v-model="language">
      <option value="en">English</option>
      <option value="es">Spanish</option>
      <option value="de">German</option>
      <option value="fr">French</option>
      <option value="it">Italian</option>
      <option value="ru">Russian</option>
      <option value="zh">Chinese</option>
      <option value="ja">Japanese</option>
    </select>
    <input class="btn btn-primary" type="submit" value="Translate">
  </form>
</template>

<script>
  export default {

    data(){
      return {
        textToTranslate:'',
        language:''
      }
    },

    created() {
      this.language = 'en';
    },

    methods: {
      formSubmit(e){
        this.$emit('formSubmit', this.textToTranslate, this.language);
        e.preventDefault();
      }
    }

  }
</script>