<template>
    <div class="container-fluid">
      <div class="row"> 
        <div class="col-lg-12">
          <div class="my-3">
            <form @submit.prevent="getBuku">
            <input
              v-model="keyword"
              type="search"
              class="form-control rounded-5"
              placeholder="mau baca apa hari ini?"
              />
            </form>
          </div>
          <div class="my-3 text-muted">menampilkan 4 dari 125</div>
          <div class="row justify-content-evenly">
            <div v-for="(Buku, i) in books" :key="i" class="col-lg-2">
            <nuxt-link :to="`/Buku/${Buku.id}`">
                <div class="card mb-3">
                  <div class="card-body">
                    <img :src="Buku.cover" class="cover" :alt="Buku.judul" />
                  </div>
                </div>
              </nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </div>
      <nuxt-link to="/">
        <button type="submit" class="btn btn-light btn-lg rounded-5 px-5">kembali</button></nuxt-link>
</template>

<script setup>
const supabase = useSupabaseClient()
const keyword = ref("")
const books = ref([])
const getBuku = async () => {
const { data, error} = await supabase.from('Buku').select('* kategori(*)')
if(data) books.value= data

}
onMounted(() => {
getBuku()
})
</script>

<style scoped>
.cover {
    width: 100%;
}
</style>