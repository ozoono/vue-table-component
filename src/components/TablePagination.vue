<template>
  <div class="ozn-paginator" :class="alignClass">
    <template v-if="paginationOptions.visualStyle === 'select'">
      <span>Page </span> 
      <select @change="onChange">
        <option 
          v-for="index in totalPages" 
          :value="index" 
          :key="index"
          :selected="index == page"
        >
          {{ index }}
        </option>
      </select>
      <span> of {{ totalPages }}</span>       
    </template>
    <template v-else>
        <button class="ozn-prev" v-if="prevPage > 0" @click="goToPage(prevPage)"><i class="icofont-caret-left"></i></button>
        <span>Page <strong>{{page}}</strong> of {{ totalPages }}</span> 
        <button class="ozn-next" v-if="nextPage <= totalPages" @click="goToPage(nextPage)"><i class="icofont-caret-right"></i></button>
    </template>
  </div>
</template>

<script>

export default {
  name: 'TablePagination',  
  props: {
    page : Number,
    totalPages: Number,
    paginationOptions: Object
  },
  data(){
    return{
    }
  },
  computed:{
    prevPage() {
      return this.page - 1;
    },
    nextPage() {
      return this.page + 1;
    },
    alignClass(){
      return `ozn-${this.paginationOptions.align}`
    }   
  },
  methods:{
    goToPage(newPage) {      
      this.$emit('new-page', parseInt(newPage))
    },
    onChange(event) {
      this.goToPage(event.target.value)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
button {
  font-size: 1rem; 
  display: inline-block;
  vertical-align: middle;
  cursor: pointer;
}
.ozn-left{
  text-align: left;
}
.ozn-right{
  text-align: right;
}
.ozn-center{
  text-align: center;
}
.ozn-prev{
  margin-right: .5rem; 
}
.ozn-next{
  margin-left: .5rem;    
}
  // Default paginator styles
.ozn{
  .ozn-paginator{
    margin: .5em 0;
    span{
      display: inline-block;
      vertical-align: middle;
    }
    button{
      border: 1px solid #ccc;
      outline: none;
      background-color: #fff; 
    } 
    select{
      margin: 0 10px;    
      border: 1px solid #ccc;
      outline: none;
      background-color: #fff;
    }
  }
}


</style>
