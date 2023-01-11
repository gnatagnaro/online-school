<template>
  <div class="detailswrapper wrapper">
    <div v-if="obj" class="detailsobj obj">
      <div class="objbox">
        <p class="objtitle">{{ obj.name }}</p>
        <p class="objdate">{{ obj.date }}</p>
        <div class="objbanner">
          <img class="objimg" :src="`/img/${obj.img}`" />
        </div>
        <p class="objdesc">{{ obj.desc }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    fetchElements: [],
    obj: null,
  }),
  async mounted() {
    try {
      await fetch("/api/main.json")
        .then((response) => response.json())
        .then((data) => (this.fetchElements = data));
      this.obj = this.fetchElements.filter(
        (objInfo) => objInfo.id == this.$route.params.id
      );
      this.obj = this.obj[0];
    } catch (e) {
      console.log(e);
    }
  },
};
</script>

<style>
.reviewinner {
  margin-top: 12px;
  border-bottom: 1px solid black;
}

.reviewtext {
  font-size: 0.9rem;
}

.reviewtextarea {
  border: 1px black solid;
  height: 80px;
  padding: 8px;
  border-radius: 8px;
}

.down-boxheadding {
  font-size: 1.4rem;
}

.reviewsdown-box {
  padding: 20px;
}

.reviewsup-box {
  display: flex;
  flex-direction: column;
  padding: 20px;
}

.reviews-centered {
  text-align: center;
}

.reviewsheadding {
  font-size: 1.3rem;
  margin-bottom: 40px;
}

.reviews {
  margin-top: 70px;
}
.reviewserror {
  color: red;
  font-size: 0.8rem;
}

.details {
  margin-top: 100px;
}

.wrapper {
  max-width: 1200px;
  margin: 0 auto;
}

.objbox {
  display: flex;
  flex-direction: column;
  text-align: center;
  padding: 20px;
  border-radius: 8px;
  box-shadow: inset 0 -3em 3em rgba(0, 0, 0, 0.1), 0 0 0 2px rgb(0, 0, 0, 0.1),
    0.3em 0.3em 1em rgba(0, 0, 0, 0.3);
}

.objtitle {
  font-size: 2.3rem;
}

.objimg {
  margin-top: 40px;
  width: 600px;
  height: 400px;
}

.objbutton {
  background-color: #009688;
  color: white;
  padding: 8px 4px;
  margin-top: 70px;
  border-radius: 8px;
}

.reviewbutton {
  border-radius: 8px;
  background-color: #009688;
  color: white;
  padding: 8px 10px;
  margin-top: 15px;
}

.objdate {
  font-size: 0.7rem;
}

.obj__desc {
  margin-top: 15px;
}

.v-application p {
  margin-bottom: 0;
}
</style>
