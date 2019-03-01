<template>
  <div id="translateForm" class="row">
   <div class="col-md-6 centerform">
    <form id="transForm" @submit="formSubmit" class="form-inline">
    	<input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word...">
    	<select class="form-control" v-model="language">
    	    <option value="sr">Serbian</option>
    	    <option value="es">Spanish</option>
    	    <option value="de">German</option>
    	    <option value="pt">Portuguese</option>
    	    <option value="ru">Russian</option>
    	    <option value="it">Italian</option>
    	    <option value="fr">French</option>
    	  </select>
    	  <input type="submit" value="Translate" class="btn btn-primary">
      </form>
      </div>
    </div>
  
</template>

<script>

export default {
  name: 'translateForm',
	data(){
		return {
		  textToTranslate: '',
      language: ''
		}
	},
  created() {
      this.language = 'sr';
  },
  methods: {
    formSubmit(e){
      this.$emit('formSubmit', this.textToTranslate, this.language)
      e.preventDefault();
    }
  }
	
}
</script>

<style>
  #transForm {
    margin: auto;
    border-radius: 10px;
    border: 1px solid #eee;
    padding: 50px;
  }
  .centerform {
    margin: auto;
  }
  
</style>
