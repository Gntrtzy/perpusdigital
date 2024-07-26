<template>
  <div class="container-fluid">
      <div class="row">
          <div class="col-lg-12">
              <h2 class="text-center my-4">ISI BUKU KUNJUNGAN</h2>
              <form @submit.prevent="kirimData">
                  <div class="mb-3">
                      <input v-model="form.nama" type="text" class="form-control form-control-lg rounded-5" placeholder="NAMA...">
                  </div>
                  <div class="mb-3">
                      <select v-model="form.keanggotaan" class="form-control form-control-lg form-select rounded-5">
                          <option value="">KEANGGOTAAN</option>
                          <option v-for="(member,i) in members" :key="i" :value="member.id">{{member.nama }}</option>
                      </select>
                  </div>
                  <div class="mb-3" v-if="form.keanggotaan == '1'">
                      <div class="row">
                          <div class="col-md-4">
                              <select v-model="form.tingkat" class="form-control form-control-lg form-select rounded-5 mb-2">
                                  <option value="">TINGKAT</option>
                                  <option value="X">X</option>
                                  <option value="XI">XI</option>
                                  <option value="XII">XII</option>
                              </select>
                          </div>
                          <div class="col-md-4">
                              <select v-model="form.jurusan" class="form-control form-control-lg form-select rounded-5 mb-2">
                                  <option value="">JURUSAN</option>
                                  <option value="PPLG">PPLG</option>
                                  <option value="TJKT">TJKT</option>
                                  <option value="TBSM">TBSM</option>
                                  <option value="DKV">DKV</option>
                                  <option value="TOI">TOI</option>
                              </select>
                          </div>
                          <div class="col-md-4">
                              <select v-model="form.kelas" class="form-control form-control-lg form-select rounded-5 mb-2">
                                  <option value="">KELAS</option>
                                  <option value="1">1</option>
                                  <option value="2">2</option>
                                  <option value="3">3</option>
                                  <option value="4">4</option>
                              </select>
                          </div>
                       </div>
                  </div>
                  <div class="mb-3">
                      <select v-model="form.keperluan" class="form-control form-control-lg form-select rounded-5">
                          <option value="">KEPERLUAN</option>
                          <option v-for="(keperluan,i) in objectives" :key="i" :value="keperluan.id">{{keperluan.nama }}</option>
                      </select>
                  </div>
                  <div class="d-flex justify-content-between">
                      <button type="submit" class="btn btn-primary btn-lg rounded-5 px-5">Kirim</button>
                      
                      <nuxt-link to="/" class="btn btn-danger btn-lg rounded-5 px-5">
                      back
                      </nuxt-link>
                  </div>
                  
              </form>
          </div>
      </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])

const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})
const kirimData = async () => {
    console.log(form.value)
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if(!error) navigateTo('/pengunjung')
}

const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if(data) members.value = data
}
const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if(data) objectives.value = data
}
onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})

</script>