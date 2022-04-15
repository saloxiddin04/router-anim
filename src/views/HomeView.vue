<template>
  <img src="../assets/images/bg.jpg" alt="" class="bg page">
  <div class="home page">
    <h1>Hi i'm, Salokhiddin
      <span class="typed-text">{{ typeValue }}</span>
      <span class="cursor" :class="{ 'typing': typeStatus }">&nbsp;</span>
    </h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus delectus impedit quas quasi tempora
      voluptates. Alias aliquam architecto, aspernatur assumenda dicta modi, molestiae nobis obcaecati perspiciatis
      possimus quo repellendus sapiente!
    </p>
  </div>
</template>

<script>
import '../assets/css/home.css'

export default {
  name: 'HomeView',
  components: {},

  data: () => {
    return {
      typeValue: '',
      typeStatus: false,
      typeArray: ['frontend', 'developer'],
      typingSpeed: 200,
      erasingSpeed: 100,
      newTextDelay: 2000,
      typeArrayIndex: 0,
      charIndex: 0
    }
  },
  methods: {
    typeText() {
      if (this.charIndex < this.typeArray[this.typeArrayIndex].length) {
        if (!this.typeStatus)
          this.typeStatus = true;
        this.typeValue += this.typeArray[this.typeArrayIndex].charAt(this.charIndex);
        this.charIndex += 1;
        setTimeout(this.typeText, this.typingSpeed);
      } else {
        this.typeStatus = false;
        setTimeout(this.eraseText, this.newTextDelay);
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus)
          this.typeStatus = true;
        this.typeValue = this.typeArray[this.typeArrayIndex].substring(0, this.charIndex - 1);
        this.charIndex -= 1;
        setTimeout(this.eraseText, this.erasingSpeed);
      } else {
        this.typeStatus = false;
        this.typeArrayIndex += 1;
        if (this.typeArrayIndex >= this.typeArray.length)
          this.typeArrayIndex = 0;
        setTimeout(this.typeText, this.typingSpeed + 1000);
      }
    }
  },
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200);
  }
}
</script>
