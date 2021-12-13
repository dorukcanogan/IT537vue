<template>
  <div class="top">
    <b-container >
     <b-row v-for="i in Math.round(topheadlines.length/2)" :key="i" class="row" align-v="center">
                        <b-col >
                          <a :href="topheadlines[2*i-2].url"> <img class="image" :src="topheadlines[2*i-2].urlToImage" alt="Fotoğraf Eklenmemiş" ></a>
                        </b-col>
                        <b-col >
                          <span class="text" v-text="topheadlines[2*i-2].title"> </span>
                        </b-col>
                        <b-col v-if= "2*i < topheadlines.length+1">
                          <a :href="topheadlines[2*i-1].url"><img class="image" :src="topheadlines[2*i-1].urlToImage" alt="Fotoğraf Eklenmemiş" ></a>
                        </b-col>
                        <b-col v-if= "2*i < topheadlines.length+1" >
                          <span class="text" v-text="topheadlines[2*i-1].title"> </span>
                        </b-col>
                  </b-row>

    </b-container>
  </div>
</template>

<script>
export default {
  name: 'topheadlines',
  props:['topheadlines'],
  data() {
    return {
      

    }
  }

}
</script>

<style scoped>
.row
{
  margin-top :1%;
  height:90%;
  border-radius: 8px;
  
  
   
}
.image{
  float: left;
  width: 90%;
  border-radius: 8px;

}

.top{
  
}


</style>
