<template>
<div>

<section id="home" class="w3l-banner py-5">
    <div class="container">
        <div class="row align-items-center">
            <div class="col-lg-6 col-sm-12 mt-lg-0 mt-4">
                <span class="title-small">Hello</span>
                <h1 class="mb-2 title"> <span>I'm</span> {{data.main.name}} </h1>
                <p>{{data.main.occupation}}
                </p>
                <div class="mt-sm-5 mt-4">
                    <a href="#contact" class="btn btn-primary btn-style mr-2" > Hire Me </a>
                    <!-- <a href="#contact"  class="btn btn-outline-primary btn-style mr-2" > Portfolio </a> -->
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

<!-- about -->
<section class="w3l-aboutblock1" id="about">
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
                    <div class="my-info mt-4">
                        <div class="single-info"><span>Name:</span>
                            <p>{{data.main.name}}</p>
                        </div>
                        <div class="single-info"><span>Age:</span>
                            <p>{{data.main.age}}</p>
                        </div>
                        <div class="single-info"><span>From:</span>
                            <p>{{data.main.address.city}}, {{data.main.address.state}}</p>
                        </div>
                        <div class="single-info"><span>Email:</span>
                            <p><a :href="data.main.email">{{data.main.email}}</a></p>
                        </div>
                    </div>
                    <div class="my-social mt-lg-5 mt-4">
                        <a :href="data.main.resumedownload" target="_blank" class="btn btn-style btn-primary">Download CV</a>
                        <ul class="social m-0 p-0">
                            <li v-for="social in data.main.social" :key="social.name">
                                <a :href="social.url"><span :class="social.className"></span></a>
                            </li>
                          </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- skills -->
<section class="w3l-skills">
        <div class="container py-lg-5">
            <h5 class="title-small text-center">Skills</h5>
            <h3 class="title-big text-center mb-sm-5 mb-4">What I do for you</h3>
            <div class="row">
                    <div class="col-md-4 col-sm-12 col-xs-12" v-for="service in data.services.services" :key="service.title">
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
        </div>
</section>

<!-- work experience -->
<section class="w3l-work-education py-5">
        <div class="container">
            <h5 class="title-small text-center">Work</h5>
            <h3 class="title-big text-center mb-sm-5 mb-4">My Work Experience</h3>
            <div class="row">
                <div class="col-lg-6 item" v-for="work in data.resume.work" :key="work.title">
                    <div class="card">
                        <div class="box-wrap">
                            <div class="icon">
                                <span class="fa fa-briefcase"></span>
                            </div>
                            <h4><b>{{work.title}}</b></h4>
                            <p>
                                Company : {{work.company}}<br>
                                Year : {{work.years}}<br>
                                Description : {{work.description}}<br>
                            </p>
                        </div>
                    </div>
                </div>
        </div>
    </div>
</section>

<!-- education -->
<section class="w3l-work-education">
        <div class="container py-lg-2">
            <h5 class="title-small text-center">Education</h5>
            <h3 class="title-big text-center mb-sm-5">My Educations</h3>
            <div class="row">
                <div class="col-lg-6 item" v-for="education in data.resume.education" :key="education.degree">
                    <div class="card">
                        <div class="box-wrap">
                            <div class="icon">
                                <span class="fa fa-graduation-cap"></span>
                            </div>
                            <h4><b>{{education.degree}}</b></h4>
                            <p>
                                School : {{education.school}}<br>
                                Graduated : {{education.graduated}}<br>
                                Description : <b>{{education.title}}</b> {{education.description}}<br>
                            </p>
                        </div>
                    </div>
                </div>
            </div>
    </div>
</section>

<!-- tech stacks -->
<section class="w3l-tech-stacks py-2">
    <div class="container">
        <h5 class="title-small text-center">Skills</h5>
        <h3 class="title-big text-center mb-sm-5 mb-4">Tech Stacks</h3>
        <div class="row">
            <div v-for="skill in data.services.skills" :key="skill.title">
                <div class="stack-item">
                    <div class="stack-card">
                        <img :src="skill.image" alt="Skill Logo">
                        <h4>{{ skill.title }}</h4>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- projects -->
<section class="w3l-projects py-5" id="projects">
        <div class="container py-lg-5">
            <h5 class="title-small text-center">Projects</h5>
            <h3 class="title-big text-center mb-sm-5">Featured Projects</h3>
            <div class="row">
                    <!-- <div class="col-md-4 col-sm-12 col-xs-12" v-for="project in data.portfolio.projects" :key="project.title"> -->
                    <div v-for="project in data.portfolio.projects" :key="project.title">
                        <div class="item">
                            <div class="card">
                                <div class="box-wrap">
                                    <div class="icon">
                                        <span class="fa fa-pencil-square-o"></span>
                                    </div>
                                    <h4 class="number">{{project.no}}</h4>
                                    <a :href="project.url" target="_blank">
                                    <h4><b>{{project.title}}</b></h4>
								    </a>
                                    <p>{{ project.description }}</p>
                                    <br>
                                    <p><span style="background-color: yellow; padding: 2px 5px; font-style: italic;">For company use only.</span></p>
                                    <div class="tech-stack-icons">
                                        <div v-for="tech in project.technologies" :key="tech.title" class="tech-icon">
                                            <img :src="tech.image" :alt="tech.title + ' Logo'">
                                        </div>
                                </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            <div class="my-social text-center">
                <a href="https://github.com/hwrd2000?tab=repositories" target="_blank" class="btn btn-style btn-primary iconify">View more on GitHub</a>
            </div>
        </div>
</section>

<!-- contact -->
<section class="w3l-contact-1 py-5" id="contact">
        <div class="container">
            <h5 class="title-small text-center">Contact</h5>
            <h3 class="title-big text-center mb-sm-5">Contact me here</h3>
            <div class="d-grid contact-view">
                <div class="cont-details">
                    <div class="cont-top">
                        <div class="cont-left text-center">
                            <span class="fa fa-phone text-primary"></span>
                        </div>
                        <div class="cont-right">
                            <h6>Call Me</h6>
                            <p><a :href="'tel:'+data.main.phone">{{data.main.phone}}</a></p>
                        </div>
                    </div>
                    <div class="cont-top margin-up">
                        <div class="cont-left text-center">
                            <span class="fa fa-envelope-o text-primary"></span>
                        </div>
                        <div class="cont-right">
                            <h6>Email Me</h6>
                            <p><a :href="'mailto:'+data.main.email" class="mail">{{data.main.email}}</a></p>
                        </div>
                    </div>
                    <div class="cont-top margin-up">
                        <div class="cont-left text-center">
                            <span class="fa fa-map-marker text-primary"></span>
                        </div>
                        <div class="cont-right">
                            <h6>Location</h6>
                            <p>{{data.main.address.street}} {{data.main.address.city}}, {{data.main.address.state}}, {{data.main.address.zip}}.</p>
                        </div>
                    </div>
                </div>
                <div class="map-content-9">
                    <div class="cont-top" v-for="social in data.main.social" :key="social.name">
                        <div class="cont-left text-center">
                            <span :class="social.className"></span>
                        </div>
                        <div class="cont-right">
                            <h6>{{social.name}}</h6>
                            <p><a :href="social.url"><font size="2px">{{social.url}}</font></a></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
</section>

<div class="map-iframe">
    <iframe
        :src="data.main.mapaddress"
        width="100%" height="400" frameborder="0" style="border: 0px;" allowfullscreen=""></iframe>
</div>

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