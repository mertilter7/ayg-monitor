<template>
<div class="bdy">
     <div class="bg-red-700 spec-b text-white">
     <div class="flex items-center justify-center p-1">
       <div>
         <img src="@/assets/img/ayg1.png" alt="ayg-logo">
       </div>
       <!-- <div class="font-bold text-xl">AY YILDIZ GAMING SERVER BİLGİLERİ GORUNTULEME PANELİ</div> -->
     </div>
   </div>
<div class="flex justify-between mt-2">
  <div id="first-content">
  <div class="flex justify-between items-center ml-10">
      <div  class="flex flex-col items-center bg-red-700 p-0.5 my-1 rounded-md">
    <h1 class="font-bold text-lg text-white">💥 Aktif Oyuncular 💥</h1>
       <div v-for="(item, i ) in myData" :key="i">
    <ol v-for="(player, i) in item" :key="i" class="bg-gray-100">
      <li :class="[player.Name == 'nKuz1'  ? 'text-red-700 font-semibold text-sm my-1 p-0.5' : 'font-semibold text-sm my-1 p-0.5']">
        <div class="flex justify-evenly gap-24 items-center">
          <div class="w-40 overflow-hidden whitespace-nowrap text-ellipsis">🎮 {{player.Name}}</div>
          <div class="text-sm ml-5">aktif olduğu süre : <span class="text-sm text-red-600">{{player.TimeF}}⏰</span></div>
          <div class="text-sm">Toplam Oyn. Dk: <span class="text-sm text-red-600">{{player.Time}}</span></div>
        </div>
        </li>
    </ol> 
  </div>
  <div>
  </div>
  <div v-for="(players, i) in myData" :key="i" class="p-2 self-end">
    <span class="text-white">Aktif Oyuncu Sayısı: {{players.length}}</span>
    <button @click="getData()" class="bg-white text-red-700 py-1 font-semibold px-2 rounded-lg text-white ml-5 focus:outline-none">Yenile</button>
  </div>
  </div>
  </div>
 </div>
<div id="second-content" class="">
   <ul  class="p-3 my-2 ml-96 flex flex-col align-center bg-white rounded-md w-3/5"> 
      <li class="text-lg text-red-600 font-bold text-center">💥{{serverData.HostName}}💥</li>
      <li class="text-base text-red-600 font-bold"><span class="text-black">🔴 Oyun Adı : </span>{{serverData.ModDesc}}</li>
      <li class="text-base text-red-600 font-bold"><span class="text-black">🔴 Aktif Harita : </span>{{serverData.Map}}</li>
      <li class="text-base text-red-600 font-bold"><span class="text-black">🔴 Aktif Oyuncu Sayısı : </span>{{serverData.Players}} / {{serverData.MaxPlayers}}</li> 
      <li class="text-base text-red-600 font-bold"><span class="text-black">🔴 Ip Adresi : </span>45.10.56.3:{{serverData.GamePort}}</li> 
      <li class="text-base text-red-600 font-bold"><span class="text-black">🔴 İzleyiciler : </span>{{serverData.SpecName}}</li> 
 </ul>
 <div class="p-3 ml-96 my-2 flex flex-col align-center bg-white rounded-md w-3/5">
   <h2 class="text-center text-lg font-bold">🎮 Sunucu Yönetim 🎮</h2>
   <span class="text-xl text-red-600 font-semibold">👑 EasT_</span>
   <span class="text-xl text-red-600 font-semibold">👑 7yearss</span>
   <span class="text-xl text-red-600 font-semibold">👑 Itachi</span>
   <span class="text-xl text-red-600 font-semibold">👑 Honeybadger</span>
   <span class="text-xl text-red-600 font-semibold">👑 Roll</span>
   <span class="text-xl text-red-600 font-semibold">👑 TraiNee</span>
   <span class="text-xl text-red-600 font-semibold">👑 NOWSK1SS</span>
  <h2 class="text-center text-xl font-bold">🎮 Adminler 🎮</h2>
  <span class="text-blue-600 font-semibold mt-2">
   🎈  nKuz1 , baranerfb , Dea , NOWSKİ , woox , farkhunda , kapo , R1vaLeN- , SaGo , Rip , ThiTemi 🎈
  </span>
 </div>
</div>
</div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data() {
    return {
      myData: [],
      serverData: {},
    }
  },
  methods: {
    getData() {
      axios
      .get("/api/" , {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-Type': 'aplication/json'
        }
      })
      .then(resp => (this.myData = resp.data.data))
    },
  getServerData() {
    axios
    .get("/api2/", {
      headers: {
        'Access-Control-Allow-Origin': '*',
        'Content-Type': 'aplication/json'
      }
    })
    .then(resp => {
      this.serverData = resp.data.data[0]
    })
},
  },
  mounted(){
    this.getData()
    this.getServerData()
  }
}
</script>
<style>
.bdy {
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
}
.bdy {
  background-image: url('../assets/img/bgcs8.jpg');
  background-repeat: no-repeat;
  height: 100vh;
}
.spec-h{
  height: 700px;
}
.spec-b{
  border-bottom-right-radius: 75px;
  border-bottom-left-radius: 75px;
}
</style>
