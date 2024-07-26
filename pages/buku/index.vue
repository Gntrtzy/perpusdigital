<template>
    <div class="container-fluid">
     <div class="row mt-5">
          <div class="col-md-3 card">
            <form @submit.prevent="getBooks">
              <input
                v-model="keyword"
                type="search"
                class="form-control rounded-8"
                
                placeholder="mau baca apa hari ini?"
              />
            </form>
          </div>
          <div class="my-3 text-muted">menampilkan {{ books.length }} buku dari {{ books.length }}</div>
          <div class="row">
            <div v-for="(book, i) in books" :key="i" class="col-lg-2">
              <nuxt-link :to="`/buku/${book.id}`">
                <div class="card mb-3">
                  <div class="card-body">
                    <img :src="book.cover" class="cover" alt="cover" />
                  </div>
                </div>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>    
  </template>
  
<script setup>
const supabase = useSupabaseClient();
const books = ref([]);
const bookcount = ref([]);
const keyword = ref('');
  
const getBooks = async () => {  
    console.log(books.value)
const { data, error } = await supabase
    .from("buku")
    .select(`*, kategori_buku(*)`)
    .ilike("judul", `%${keyword.value}%`);
    if(data) books.value = data;
};


const countBook = async () => {
const { data, count } = await supabase
    .from("buku")
    .select("*", { count: "exact" });
    if (data) bookcount.value = count;
  };
  
onMounted(() => {
    getBooks();
    countBook()
  });
</script>

<style>
.cover {
    width: 40%;
}

.card {
    width: 100%;
    height: 100%;
}
</style>