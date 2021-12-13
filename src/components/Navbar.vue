<template>
   <div>
  <b-navbar toggleable="lg" type="dark" variant="warning">
    <b-navbar-brand><b><router-link to="/">Haber Dünyası  |</router-link></b></b-navbar-brand>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
    
    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#" active><router-link to="/finance">Finans</router-link></b-nav-item>
        <b-nav-item href="#"><router-link to="/health">Sağlık</router-link></b-nav-item>
        <b-nav-item href="#"><router-link to="/science">Bilim</router-link></b-nav-item>
        <b-nav-item href="#"><router-link to="/sports">Spor</router-link></b-nav-item>
        <b-nav-item href="#"><router-link to="/technology">Teknoloji</router-link></b-nav-item>
        <b-nav-item href="#"><router-link to="/entertainment">Eğlence</router-link></b-nav-item>
        
        <b-dropdown text="Dünyadan Haberler" size="sm" variant="outline-primary">
        <b-dropdown-item @click="countrychange('gb')"><router-link to="/worldnews">İngiltere</router-link></b-dropdown-item>
        <b-dropdown-item @click="countrychange('us')"><router-link to="/worldnews">ABD</router-link></b-dropdown-item>
        <b-dropdown-item @click="countrychange('de')"><router-link to="/worldnews">Almanya</router-link></b-dropdown-item>
        <b-dropdown-item @click="countrychange('fr')"><router-link to="/worldnews">Fransa</router-link></b-dropdown-item>
      </b-dropdown>
      </b-navbar-nav>

      <b-navbar-nav class="ml-auto">
        <b-nav-form @submit.prevent="false">
          <b-form-input v-model="query" @keydown.enter.native="doSearch" placeholder="Haberlerde Arayın.."></b-form-input>
          <b-button variant="outline-primary" @click="doSearch"><router-link to="/search">Ara</router-link></b-button>
        </b-nav-form>
        <b-avatar variant="warning" icon="people-fill"></b-avatar>
        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>Oturum Aç</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
import Vue from "vue";
export default {
  name: 'Navbar',
  props:{
      handleRequest: Function
  },
  data() {
    return {
      query:''
    }
  },
  methods:{
      countrychange(query){
         this.handleRequest(query);
      },
      doSearch(){
        this.$router.push({path: '/search'});
        this.$emit('SearchRequest', this.query);
    },
  }

}
</script>


<style>

    b-navbar-brand{
        margin-top: 100px;
        background-color:lightblue;
    }

</style>