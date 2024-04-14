<template >
  <div class="main flex flex-col gap-1 w-screen h-screen bg-gradient-to-b from-blue-300 to-blue-200 overflow-y-hidden overflow-x-auto">
    <div class="top-container">
      <div class="logo w-40">
        <img src="../../assets/vedas.png" alt="vedas logo" />
      </div>
      <div class="leftmost-icons flex justify-around gap-3">
        <div class="back-button shadow-2xl rounded-full cursor-pointer mt-10 px-2 h-10 flex items-center justify-center" @click="$router.push('/')">
          <i class="fa-solid fa-circle-left text-4xl"></i>
        </div>
        <div class="home w-10 h-10 text-1xl rounded-full mt-10 px-2 cursor-pointer flex items-center justify-center" @click="$router.push('/')">
          <i class="fa-solid fa-house "></i>
        </div>
        <div class="user">
          <img class="user-button" src="../../assets/userbg.png" alt="user-image" />
        </div>
      </div>
    </div>
    <div class="flex flex-col items-center justify-center flex-1">
      <h1 class="text-4xl font-bold mb-2">RIDaM</h1>
      <div class="flex flex-col items-center mb-4">
        
        <div class="pill bg-blue-100 rounded-full p-3 shadow-md mt-3">
          <p class="text-lg font-semibold">Raster Analytics System for Interactive Data Modeling</p>
        </div>
      </div>
      <h2 class="text-xl font-semibold mb-4">Select the management module</h2>
      <ScrollableModule scrollDistance="3000" />
    </div>
    <div class="flex justify-end p-4 bg-blue-100">
      <p class="text-lg font-medium">About RIDaM</p>
    </div>
  </div>
</template>

<script>
import ScrollableModule from "../../components/Ridam-Pallete/ScrollableModule.vue";
export default {
  name: "Ridam",
  components: {
    ScrollableModule,
  },
};
</script>

<!-- No scoped styles needed, as Tailwind CSS is utility-based -->
<style scoped>
  /* Media Queries */

  .top-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0;
  
  display: flex;
  justify-content: space-between;
}
.back-button{
  color: #2756ff;
}

.logo {
  margin-right: 2em; /* Add some spacing between the logo and other content */
}

.home{
  background-color: #2756ff;
  color: #97c7fd;
}

.logo img {
  margin-left: 1em;
}

.user-button {
  width: 5rem;
  margin-top: 1rem;
  margin-right: 2rem;
  border-radius: 50%; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
}
@media screen and (max-width: 640px) {
  /* Small mobile devices */
 

}

@media screen and (min-width: 641px) and (max-width: 767px) {
  /* Big mobile devices */
 
}

@media screen and (min-width: 768px) and (max-width: 1023px) {
  /* Small laptops and tablets */
 
}

@media screen and (min-width: 1024px) and (max-width: 1279px) {
  /* Big laptops and desktops */
  
}
@media screen and (min-width: 1280px) and (max-width: 1440px) {
  /* Big laptops and desktops */

}
@media screen and (min-width: 1441px) {
  /* Big laptops and desktops */

}
</style>