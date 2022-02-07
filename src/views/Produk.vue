<template>
  <div>
    <h1>Products</h1>
    <ul v-for="produk in products" :key="produk.id">
      <li>{{produk.nama}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      products:'',
    }
  },
  mounted(){
    this.getProduk()
  },
  methods :{
    async getProduk(){
      let {data,error} = await this.$supabase
      .from('tb_produk')
      .select()
      if (data) this.products = data 
      if (error) console.error(error)
    }
  }
};
</script>

<style lang="scss" scoped></style>
