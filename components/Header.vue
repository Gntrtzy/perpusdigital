
<template>
    <div class="header">
      <div class="h-img">
        <img src="~/assets/img/LOGO-SMK4.png" alt="logo smkn 4" />
      </div>
      <div class="h-text">
        <div class="t-judul">
          <h1>PERPUS DIGITAL</h1>
          <address>
            SMKN 4 TASIKMALAYA
            <p>JL. DEPOK, SUKAMENAK, PERBARATU</p>
          </address>
        </div>
      </div>
    </div>
  </template>
  
  <style>
  .header {
    display: flex;
    align-items: center;
    background-color: #0004ff;
    color: #ffffff;
   width: 100%;
  }
  
  .h-img > img {
    width: 115px;
    height: 135px;
    margin-left: 30px;
  }
  
  .t-judul {
    margin-left: 20px;
  }
  @media (max-width: 750px) {
    .header {
      flex-direction: column;
      align-items: flex-start;
      text-align: center;
    }
  
    .h-img > img {
      width: 100px;
      height: 100px;
      margin-left: 0;
      margin-bottom: 10px;
    }
  
    .t-judul {
      margin-left: 0;
    }
  
    h1 {
      font-size: 1.5em;
    }
  }
  </style>
  