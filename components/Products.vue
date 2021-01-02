<template>
  <div class="max-w-md sm:max-w-xl lg:max-w-6xl mx-auto py-8">
    <h2 class="text-xl text-left text-gray-900">Merchants</h2>
    <section class="py-4">
      <div class="flex justify-between -mx-3 mb-2">
        <input v-model="query" @input="type = 'search'" class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="merchant" type="text" placeholder="search merchant">
        <div class="flex">
          <div class="px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-state">
              Category
            </label>
            <div class="relative">
              <select v-model="category" @change="type = 'category'" class="block appearance-none w-full bg-gray-200 border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-state">
                <option value="product">product merchant</option>
                <option value="service">service merchant</option>
              </select>
              <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
                <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
              </div>
            </div>
          </div>
          <div class="px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-state">
              Order
            </label>
            <div class="relative">
              <select v-model="order" @change="type = 'order'" class="block appearance-none w-full bg-gray-200 border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-state">
                <option value="ascending">ascending</option>
                <option value="descending">descending</option>
              </select>
              <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
                <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <div class="flex flex-wrap -mx-4">
      <div class="mt-6 w-full px-4 lg:w-1/3 xl:w-1/3" v-for="product in filteredProducts" :key="product.id">
        <Product :product="product"/>
      </div>
    </div>
  </div>
</template>

<script>
import Product from './Product.vue';
import products from '../assets/products.json';
export default {
  name: 'products',
  components:{
    Product,
  },
  data(){
    return {
      products: products,
      query: '',
      category: '',
      order: '',
      type: null,
    }
  },
  computed:{
    filteredProducts() {
        switch (this.type) {
          case 'search':
            var filter = new RegExp(this.query, 'i')
            return this.products.filter(el => el.title.match(filter))
            break;
          case 'category':
            var filter = new RegExp(this.category, 'i')
            return this.products.filter(el => el.type.match(filter))
            break;
          // case 'order':
          //   return this.products.filter(el => el.title.match(filter))
          //   break;
        
          default:
            return this.products
        }
        // if(this.type === 'search'){
        //   return this.products.filter(el => el.title.match(filter))
        // }
        // else if (this.type === 'category') {
        //   return this.product.filter(el => el.type.match(filter))
        // } else {
          
        // }
      
    },
    // categorizedProducts(){
    //   let filter = new RegExp(this.category, 'i')
    //   console.log(this.filteredProducts.filter(el => el.type.match(filter)))
    //   return this.filteredProducts.filter(el => el.type.match(filter))
    // }
  },
  methods:{
    sortProducts(type){
      switch (type === 'category') {
        case value:
          
      
        default:
      }
      let filter = new RegExp(this.category, 'i')
      console.log(this.filteredProducts.filter(el => el.type.match(filter)))
      this.filteredProducts = this.filteredProducts.filter(el => el.type.match(filter))
      // return this.filteredProducts.filter(el => el.type.match(filter))
    }
  }
}
</script>
