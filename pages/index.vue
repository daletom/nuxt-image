<template>
  <div>
    <h1 class="title-font sm:text-4xl text-3xl m-4 font-medium text-gray-900">Example using the Nuxt Image Component</h1>
    <p class="m-4 leading-relaxed">Optimize your images in your <a href="https://image.nuxtjs.org/providers/imgix" class="mt-3 text-indigo-500 inline-flex">Nuxt Image Component</a> using imgix. For more info about how this tutorial was made, you can view the accompanying <a href="https://image.nuxtjs.org/providers/imgix" class="mt-3 text-indigo-500 inline-flex">blog post</a> or you can view the code directly on <a href="https://github.com/daletom/nuxt-image" class="mt-3 text-indigo-500 inline-flex">Github.</a>  You can also find out more about the imgix parameters in the imgix <a href="https://docs.imgix.com/apis/rendering" class="mt-3 text-indigo-500 inline-flex">documenation.</a> </p>
    <div class="flex flex-wrap">
      <nuxt-img
        class="float-left p-2 m-auto w-full lg:w-1/2 xl:w-1/3 2xl:w-1/3"
        v-for="(image, index) in images"
        :key="index"
        provider="imgix"
        :src="image"
        sizes="xs:98vw sm:98vw md:98vw lg:49vw xl:31vw 2xl:31vw"
        fit="crop"
        :modifiers="{ auto: 'format,compress', ar: '1:1', ch: 'width,DPR' }"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        '/artsy/1.jpg',
        '/artsy/2.jpg',
        '/artsy/3.jpg',
        '/artsy/4.jpg',
        '/artsy/5.jpg',
        '/artsy/6.jpg'
      ]
    }
  }
}
</script>
