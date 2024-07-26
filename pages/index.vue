<script setup lang="ts">
import ChartStatistik from '~/components/ChartStatistik.vue';
</script>

<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/pengunjung/tambah">
                    <div class="card bg-pengunjung rounded-5">
                        <div class="card-body">
                            <h2>pengunjung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>           
            <div class="col-lg-6">
                <nuxt-link to="/buku/">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>cari buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
    </div>
    <h2><strong>STATISTIK</strong></h2>
<div class="Container-fluid">
    <div class="row justify-cotent-evenly rounded-3">
        <div class="col-5">
            <div class="cardi">
                <div class="skuy">
                    <h2>3 pengunjung</h2>
                </div>
            </div>
        </div>
        <div class="col-5">
            <div class="skuy1">
                <h2>180 Buku</h2>
            </div>
        </div>
    </div>
</div>
<div class="line">
    <ChartStatistik />
</div>
</template>

<style scoped>
.v2{
    height: 3px;
    width: 98%;
    margin-left: 30px;
    border-left: 3px solid black;
    background-color: black;
}
.v1 {
    margin-top: 40px;
    margin-left: 30px;
    border-left: 3px solid black;
    height: 400px;
}
.card-body {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
    background-image: url('~/assets/img/bg-home-kunjungan.jpeg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.card.bg-buku {
    background: url('~/assets/img/bg-home-cari-buku.jpg');
    background-size: cover;
    
}
.skuy{
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #E4CA6B;
}
.skuy1 {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #1DDD81
}
</style>