<template>
<div>
    
<link rel="stylesheet" type='text/css' href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css" />

<section id="home" class="w3l-banner py-5">
    <div class="container">
        <div class="row align-items-center">
            <div class="col-lg-6 col-sm-12 mt-lg-0 mt-4">
                <span class="title-small">Hello</span>
                <h1 class="mb-2 title"> <span>I'm</span> {{data.main.name}} </h1>
                <p>{{data.main.occupation}}
                </p>
                <div class="mt-sm-5 mt-4">
                    <nuxt-link to="/Contact" class="btn btn-primary btn-style mr-2" > Hire Me </nuxt-link>
                    <nuxt-link to="/Contact" class="btn btn-outline-primary btn-style mr-2" > Portfolio </nuxt-link>
                </div>
            </div>
            <div class="col-lg-6 col-md-8 col-sm-10 mt-lg-0 mt-4">
                <div class="img-effect text-lg-center">
                    <img :src="data.main.image" alt="myphoto" class="img-fluid">
                </div>
            </div>
        </div>
    </div>
</section>


<section class="w3l-index3" id="about">
    <div class="midd-w3 py-5">
        <div class="container py-lg-5 py-md-3">
            <div class="row">
                <div class="col-lg-4">
                    <div class="position-relative">
                        <img :src="data.main.fullimage" alt="" class="radius-image img-fluid">
                    </div>
                </div>
                <div class="col-lg-8 mt-lg-0 mt-5">
                    <h5 class="title-small mb-2">Who am i?</h5>
                    <h3 class="title-big">I'm <b>{{data.main.name}}</b>, a {{data.main.occupation}}</h3>
                    <p class="mt-4">{{data.main.bio}}</p>
                    <a :href="data.main.resumedownload" target="_blank" class="btn btn-style btn-primary mt-lg-5 mt-4">Download CV</a>
                </div>
            </div>
        </div>
    </div>
</section>

<section class="w3l-services">
    <div class="blog" id="services">
        <div class="container py-lg-5">
            <h5 class="title-small text-center">Skills</h5>
            <h3 class="title-big text-center mb-sm-5 mb-4">What I do for you</h3>
            <div class="row">
                
                    
                    <div class="col-md-4 col-sm-12 col-xs-12" v-for="service in data.services.services" v-bind:key="service">
                        <div class="item">
                            <div class="card">
                                <div class="box-wrap">
                                    <div class="icon">
                                        <span class="fa fa-pencil-square-o"></span>
                                    </div>
                                    <h4 class="number">{{service.no}}</h4>
                                    <h4><a >{{service.title}}</a></h4>
                                    <p>{{service.description}}</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    

            </div>
            <div class="mt-5 text-more">
                <p class="mt-4 pt-3 sample text-center">
                    
                </p>
            </div>
        </div>
    </div>
</section>

<section class="w3l-services">
    <div class="blog" id="services">
        <div class="container">
            <h5 class="title-small text-center">Skills</h5>
            <h3 class="title-big text-center mb-sm-5 mb-4">Tech Stacks</h3>
            <div class="row">
                <div class="col-md-4 col-sm-12 col-xs-12" v-for="skill in data.services.skills" :key="skill">
                    <div class="item">
                        <div class="card text-center">
                            <div class="box-wrap">
                                <img :src="skill.image" alt="Skill Logo" width="80" height="80">
                                <h4 class="skill-title">{{ skill.title }}</h4>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="mt-5 text-more">
                <p class="mt-4 pt-3 sample text-center"></p>
            </div>
        </div>  
    </div>
</section>

 <section class="w3l-grid-quote text-center py-5">
   <div class="container py-3">
     <h6 class="title-small">Get in touch</h6>
     <h3 class="title-big mb-md-5 mb-4">Let's start a Project! Hire Me.</h3>
     <router-link to="/contact" class="btn btn-style btn-primary mr-2">Hire Me </router-link>
     <router-link to="/contact" class="btn btn-style btn-outline-primary">Get in touch</router-link>
   </div>
 </section>



</div>
</template>

<script>
import data from '~/static/api/data.json'
export default {
    
    name:"index",
    data(){
        return {
            data:data,
			
        }
    },
    head() {
      return {
        title: this.data.main.name,
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'My custom description'
          }
        ]
      }
    }
}
</script>