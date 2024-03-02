<template>
  <MobileMenu/>
  <AppHeader/>
  <div class="css-blurry-gradient-red"></div>
  <NuxtPage data-aos="fade-in"/>
  <AppFooter/>
</template>

<script>
import AOS from 'aos';
import 'aos/dist/aos.css'; // You can also use <link> for styles
export default {
  /**
   * * Watch for route changes
   * This event is triggered when the route changes.
   * @param {Object} to - Route object
   * @param {Object} from - Route object
   */
  watch: {
    $route(to, from) {
      console.log('De', from.fullPath, 'a', to.fullPath);
    }
  },
  mounted() {
    AOS.init({
        // Global settings:
        disable: false, // accepts following values: 'phone', 'tablet', 'mobile', boolean, expression or function
        startEvent: 'DOMContentLoaded', // name of the event dispatched on the document, that AOS should initialize on
        initClassName: 'aos-init', // class applied after initialization
        animatedClassName: 'aos-animate', // class applied on animation
        useClassNames: false, // if true, will add content of `data-aos` as classes on scroll
        disableMutationObserver: false, // disables automatic mutations' detections (advanced)
        debounceDelay: 50, // the delay on debounce used while resizing window (advanced)
        throttleDelay: 99, // the delay on throttle used while scrolling the page (advanced)
        
        // Settings that can be overridden on per-element basis, by `data-aos-*` attributes:
        offset: 120, // offset (in px) from the original trigger point
        delay: 20, // values from 0 to 3000, with step 50ms
        duration: 20, // values from 0 to 3000, with step 50ms
        easing: 'ease-in-out-back', // default easing for AOS animations
        once: false, // whether animation should happen only once - while scrolling down
        mirror: false, // whether elements should animate out while scrolling past them
        anchorPlacement: 'top-bottom', // defines which position of the element regarding to window should trigger the animation
    });
  }
}
</script>

<style scoped>
.css-blurry-gradient-red {
  position: absolute;
  top: 5%;
  right: 80%;
  width: 300px;
  height: 300px;
	border-radius: 0% 0% 50% 50%;
  rotate: 10deg;
	filter: blur(100px);
  background: radial-gradient(circle at 10% 10%,rgb(188, 48, 165), rgba(186, 181, 88, 0));
  opacity: 0.5;
  z-index: 10;
}
</style>