<template>
    <div class="container-fluid">
            <div class="col-1">
                <nuxt-link to="../">
                    <i class="bi bi-arrow-left-short"></i>
                </nuxt-link>
            </div>
            <div class="col-10">
                <h2 style="
            text-align: center;
            font-family: inter;
            margin-top: 20px;
          ">
                    detail buku
                </h2>
            </div>
            <table>
                <tr>
                    <td rowspan="7"><img :src="buku.cover" class="cover" alt="cover" /></td>
                </tr>
                <tr>
                    <td >JUDUL</td>
                    <td>:</td>
                    <td >{{ buku.judul }}</td>
                </tr>
                <tr>
                    <td >PENULIS</td>
                    <td >:</td>
                    <td >{{ buku.penulis }}</td>
                </tr>
                <tr>
                    <td >PENERBIT</td>
                    <td >:</td>
                    <td >{{ buku.penerbit }}</td>
                </tr>
                <tr>
                    <td >KATEGORI</td>
                    <td >:</td>
                    <td >{{ buku.kategori.nama }}</td>
                </tr>
                <tr>
                    <td >RAK</td>
                    <td>:</td>
                    <td >{{ buku.rak.kode }}</td>
                </tr>
                <tr>
                    <td >DESKRIPSI</td>
                    <td >:</td>
                    <td>{{ buku.deskripsi }}</td>
                </tr>
            </table>
        </div>
</template>


<script setup>
const supabase = useSupabaseClient()
const buku = ref({})

const getBookById = async () => {
    const { data, error } = await supa.from('buku').select(`*, kategori_buku(*), rak(*)`)
        .eq('id', route.params.id)
    if (data) {
        console.log(data[0])
        buku.value = data[0]
        loading.value = false
    }
}

onMounted(() => {
    getBookById()
})
</script>

<style scoped>
img {
    width: 300px;
    height: 400px;
}

button {
    text-align: center;
    color: black;
    font-family: inter;
}

table {
    font-size: 30px;
}
i {
  font-size: 60px;
  color: #000000
}

</style>