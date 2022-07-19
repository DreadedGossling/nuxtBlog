---
author:
  name: Benjamin
  bio: All about Benjamin
  image: https://images.unsplash.com/photo-1533636721434-0e2d61030955?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=550&q=80

title: My first Blog Post
description: Learning how to use @nuxt/content to create a blog
img: https://images.unsplash.com/reserve/LJIZlzHgQ7WPSh5KVTCB_Typewriter.jpg?ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=60
alt: my first blog post
---


  <!-- <author :author="author"></author> -->





# My first blog post

Welcome to my first blog post using content module


## This is a heading

This is some more info

### This is a sub heading

This is some more info

### This is another sub heading

This is some more info

## This is another heading

This is some more info


<info-box>
  <template #info-box>
    This is a vue component inside markdown using slots
  </template>
</info-box>


<div class="text">
  This is HTML inside markdown that has a class of note
</div>

export default {
  nuxt: 'is the best'
}