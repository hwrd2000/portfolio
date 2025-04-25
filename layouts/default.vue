<template>
<div>

<header id="site-header" class="fixed-top">
  <div class="container">
      <nav class="navbar navbar-expand-lg stroke">
          <button class="navbar-toggler  collapsed bg-gradient" type="button" data-toggle="collapse"
              data-target="#navbarTogglerDemo02" aria-controls="navbarTogglerDemo02" aria-expanded="false"
              aria-label="Toggle navigation">
              <span class="navbar-toggler-icon fa icon-expand fa-bars"></span>
              <span class="navbar-toggler-icon fa icon-close fa-times"></span>
              
          </button>

          <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
            <ul class="navbar-nav ml-auto">
                <li class="nav-item active">
                    <nuxt-link to="/" class="nav-link">Home <span class="sr-only">(current)</span></nuxt-link>
                </li>
                <li class="nav-item">
                    <a href="#about" class="nav-link">About</a>
                </li>
                <li class="nav-item">
                    <a href="#projects" class="nav-link">Projects</a>
                </li>
                <li class="nav-item">
                    <a href="#contact" class="nav-link">Contact</a>
                </li>
            </ul>
          </div>
          
          <div class="mobile-position">
              <nav class="navigation">
                  <div class="theme-switch-wrapper">
                      <label class="theme-switch" for="checkbox">
                          <input type="checkbox" id="checkbox">
                          <div class="mode-container">
                              <i class="gg-sun"></i>
                              <i class="gg-moon"></i>
                          </div>
                      </label>
                  </div>
              </nav>
          </div>
         
      </nav>
  </div>
</header>


<nuxt/>
 

<section class="w3l-footer py-sm-5 py-4">
  <div class="container d-flex justify-content-center">
    <div class="footer-content text-center">
        <ul class="social m-0 p-0">
            <li v-for="socaildata in data.main.social" :key="socaildata.name">
            <a :href="socaildata.url"><span :class="socaildata.className"></span></a>
          </li>
        </ul>
    </div>
</div>

  
<button
  id="movetop"
  title="Go to top"
  @mousedown="startDrag"
  @mouseup="endDrag"
  @click="handleClick"
  style="position:fixed; bottom:20px; right:20px; cursor:grab; z-index:9999; transition: left 0.05s linear, top 0.05s linear;">
  <span class="fa fa-angle-up"></span>
</button>

</section>


</div>
</template>
<script>
import data from '~/static/api/data.json'
export default {
  name: "index",
  data() {
    return {
      data: data,
      dragging: false,
      wasDragged: false,
      offsetX: 0,
      offsetY: 0,
      startX: 0,
      startY: 0,
      buttonEl: null,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    topFunction() {
      window.scrollTo({ top: 0, behavior: 'smooth' });

      // Reset button position after scroll animation
      setTimeout(() => {
        this.resetButtonPosition();
      }, 500);
    },
    handleClick(e) {
      if (!this.wasDragged) {
        this.topFunction();
      }
      this.wasDragged = false; // reset after each click attempt
    },
    startDrag(e) {
      this.buttonEl = document.getElementById("movetop");
      this.dragging = true;
      this.wasDragged = false;
      this.startX = e.clientX;
      this.startY = e.clientY;
      this.offsetX = e.clientX - this.buttonEl.offsetLeft;
      this.offsetY = e.clientY - this.buttonEl.offsetTop;

      document.addEventListener("mousemove", this.queueDrag);
      document.addEventListener("mouseup", this.stopDrag);
    },
    endDrag(e) {
      const moveX = Math.abs(e.clientX - this.startX);
      const moveY = Math.abs(e.clientY - this.startY);
      if (moveX > 5 || moveY > 5) {
        this.wasDragged = true;
      }
    },
    queueDrag(e) {
      if (this.dragging) {
        const x = e.clientX - this.offsetX;
        const y = e.clientY - this.offsetY;
        window.requestAnimationFrame(() => this.drag(x, y));
      }
    },
    drag(x, y) {
      if (this.buttonEl) {
        this.buttonEl.style.left = `${x}px`;
        this.buttonEl.style.top = `${y}px`;
        this.buttonEl.style.bottom = 'auto';
        this.buttonEl.style.right = 'auto';
      }
    },
    stopDrag() {
      this.dragging = false;
      document.removeEventListener("mousemove", this.queueDrag);
      document.removeEventListener("mouseup", this.stopDrag);
    },
    handleScroll() {
      if (window.scrollY <= 10) {
        this.resetButtonPosition();
      }
    },
    resetButtonPosition() {
      const button = document.getElementById("movetop");
      if (button) {
        button.style.left = '';
        button.style.top = '';
        button.style.bottom = '20px';
        button.style.right = '20px';
      }
    },
  },
};
</script>