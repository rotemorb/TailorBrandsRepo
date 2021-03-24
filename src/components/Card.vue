<template>
<div class="card relative flex flex-col">
  <div class="flex justify-center">
    <img :src="headerImg" alt="" >
  </div>
  <p class="ml-2 text-lg leading-6 font-medium text-gray-900">{{headline}}</p>
  <p class="mt-2 ml-2 text-base text-gray-500">
    {{subHeadline}}
  </p>
</div>
</template>

<script >
export default {   
  props: ['cardObj'],
  data() {
    return {
      headline: this.cardObj.Headline,
      subHeadline: this.cardObj["Sub-headline"],
      headerImg: this.cardObj["Header image"] ? this.cardObj["Header image"][0].url : "../src/assets/logo.png"
    };
  }
}
</script>

<style scoped>
.card
{
  background: #FFFFFF;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.14), 0px 2px 2px rgba(0, 0, 0, 0.12), 0px 1px 3px rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  object-fit: cover;
  max-width:22.5rem;
  height: 360px;
}

.card img
{
  width:360px;
  height: 202px;
}

</style>