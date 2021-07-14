In this tutorial, I am going to be creating a simple image gallery in a Nuxt project.  I will also be using Tailwind CSS and be deploying this site on Vercel.  The image gallery will be a flex design, with 3 columns on the largest screen sizes, 2 column on the smaller desktop sizes, and 1 column on mobile sizes.  The images will be using the Nuxt Image component and will contain a responsive design.  If you would like to skip the tutorial and go right to the code, you can see that in Github.  Here is also a link to a video of this tutorial:

Please start by initiating a Nuxt project and then installing the Nuxt Image Component as I explained in the beginning of this blog.  When initiating the Nuxt project, I would suggest choosing Tailwind CSS, since my examples will be using this module for css.

Once that is all set up, go to your index.vue file in your pages folder.  Erase what is currently there and start fresh with a div tag.  Like this:


    <template>
      <div>
      </div>
    </template>

You can add some sections for a headline and text at the top of your page.  Here is an example of adding this with some Tailwind CSS:


    <template>
      <div>
        <h1 class="title-font sm:text-4xl text-3xl m-4 font-medium text-gray-900">Example using the Nuxt Image Component</h1>
        <p class="m-4 leading-relaxed">Optimize your images with imgix in your Nuxt Image Component.</p>
      </div>
    </template>

Next, we can focus on adding a flex div to include your images and the nuxt-img tag.  


    <template>
      <div>
        <h1 class="title-font sm:text-4xl text-3xl m-4 font-medium text-gray-900">Example using the Nuxt Image Component</h1>
        <p class="m-4 leading-relaxed">Optimize your images with imgix in your Nuxt Image Component.</p>
        <div class="flex flex-wrap">
          <nuxt-img
            provider="imgix"
            src=""
          />
        </div>
      </div>
    </template>

Now we can add as many images inside of the flex div as we would like for our gallery.  For the next code example, I will focus on just the `<nuxt-img />` tag.


    <nuxt-img
      class="float-left p-2 m-auto w-full lg:w-1/2 xl:w-1/3 2xl:w-1/3"
      provider="imgix"
      src=""
      sizes="xs:98vw sm:98vw md:98vw lg:49vw xl:31vw 2xl:31vw"
      fit="crop"
      :modifiers="{ auto: 'format,compress', ar: '1:1' }"
    />

I have included in 2 places info about the sizing that will help my responsive design. First, in the class section.  Again, just a reminder, this is an example of using Tailwind CSS. If this is your first time encountering it, I really do suggest checking out their documentation.  On XL and 2XL size screens, the images will be viewed in css at 33% the size of the screen. Between 1024 px and 1280 px size screens, the images will be viewed in css at 50% the size of the screen. Then any screen
 smaller than 1024px wide will be viewed at 100% the size of the screen.  I have also replicated this same idea in the `sizes` attribute, which tells the Nuxt Image Component to generate resized versions for each of these scenarios.
 
 Now, you can go ahead and create as many of these `<nuxt-img>` tags as you need for your gallery.  If you are going to pass image urls from data or an API, you can easily use the v-for attribute as well.  I do believe this is one of the more powerful aspects of Nuxt, so I will go ahead and add 6 image names in my Data section and pass them as a v-for.  This could also be a great time to use the Image Management solution included with your imgix account to find the appropriate images you would like to use.  
 
 For my list of images, they are conveniently named 1 through 6, so I will place them in my `script` section of my index.vue:
 

    <script>
    export default {
      data() {
        return {
          images: [
            '/artsy/1.jpg?',
            '/artsy/2.jpg?',
            '/artsy/3.jpg?',
            '/artsy/4.jpg?',
            '/artsy/5.jpg?',
            '/artsy/6.jpg?'
          ]
        }
      }
    }
    </script>

I can now access these images using a v-for in my `<nuxt-img>`.  In order to do that, here is how I am modifying my tag:


    <nuxt-img
      class="float-left p-2 m-auto w-full lg:w-1/2 xl:w-1/3 2xl:w-1/3"
      v-for="(image, index) in images"
      :key="index"
      provider="imgix"
      :src="image"
      sizes="xs:98vw sm:98vw md:98vw lg:49vw xl:31vw 2xl:31vw"
      fit="crop"
      :modifiers="{ auto: 'format,compress', ar: '1:1' }"
    />

This will loop through my 6 images, creating a responsive img tag for each of them in my gallery.  This is a rather simple idea of using a v-for, but hopefully gives you the idea of how quickly this can be used on a large amount of images.