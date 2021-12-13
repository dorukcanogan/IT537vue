<template>
  <div class="top">
    <b-container class="cont">
            <b-row>
                  <b-col class>
                  </b-col>
                  <b-col cols="6">
                    <div>
                      <b-carousel
                        id="carousel-1"
                        controls
                        :interval="4000"
                        style="text-shadow: 1px 1px 2px #333;">
                       <b-carousel-slide>
                          <template #img>
                            <img
                              class="d-block img-fluid w-100"
                              width="1024"
                              height="480"
                              :src="imgs[0].urlToImage"
                              alt="image slot">
                             <b><p v-text="imgs[0].title"></p></b>
                          </template>
                        </b-carousel-slide>
                        <b-carousel-slide>
                          <template #img>
                            <img
                              class="d-block img-fluid w-100"
                              width="1024"
                              height="480"
                              :src="imgs[1].urlToImage"
                              alt="image slot">
                             <b><p v-text="imgs[1].title"></p></b>
                          </template>
                        </b-carousel-slide>
                        <b-carousel-slide>
                          <template #img>
                            <img
                              class="d-block img-fluid w-100"
                              width="1024"
                              height="480"
                              :src="imgs[2].urlToImage"
                              alt="image slot">
                             <b><p v-text="imgs[2].title"></p></b>
                          </template>
                        </b-carousel-slide>
                        <b-carousel-slide>
                          <template #img>
                            <img
                              class="d-block img-fluid w-100"
                              width="1024"
                              height="480"
                              :src="imgs[3].urlToImage"
                              alt="image slot">
                             <b><p v-text="imgs[3].title"></p></b>
                          </template>
                        </b-carousel-slide>
                      </b-carousel>
                    </div>
                  </b-col>
                  <b-col>
                </b-col>
           </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'carousel',
  data() {
    return {
      imgs:[]
      
    }
  },
  created() {
    const url = 'https://newsapi.org/v2/top-headlines?country=tr&pageSize=32&apiKey=098ba3055806413080e3a055f8e8c17b';
    fetch(url)
    .then((response) => {return response.json()})
    .then((response) => {
      this.imgs = response.articles;
    })

  }

}
</script>

<style scoped>

img{
width:80%;
}

p{
font-size:18px;
}

</style>
