<template lang="pug">
#dropdowns
  .large-space
  h4
    span Dropdowns
    a.chip.circle(
      @click="domain.showSamples(data, '#dropdowns button, #dropdowns .field', 'Dropdowns', null, 'https://github.com/beercss/beercss/blob/main/docs/DROPDOWN.md')"
    )
      i code
  nav.wrap
    button(data-ui="#dropdown1")
      span Default
      i arrow_drop_down
      #dropdown1.dropdown(data-ui="#dropdown1")
        a Item 1
        a Item 2
        a Item 3
    button(data-ui="#dropdown2")
      span No-wrap
      i arrow_drop_down
      #dropdown2.dropdown.no-wrap(data-ui="#dropdown2")
        a Lorem ipsum dolor sit amet
        a Lorem ipsum dolor sit amet
        a Lorem ipsum dolor sit amet
    button.circle(data-ui="#dropdown3")
      i arrow_back
      #dropdown3.dropdown.left.no-wrap(data-ui="#dropdown3")
        a Item 1
        a Item 2
        a Item 3
    button.circle(data-ui="#dropdown4")
      i arrow_forward
      #dropdown4.dropdown.right.no-wrap(data-ui="#dropdown4")
        a Item 1
        a Item 2
        a Item 3
    button(data-ui="#dropdown5")
      span Images and icons
      #dropdown5.dropdown.no-wrap(data-ui="#dropdown5")
        a Title
        a
          div Title
          label Some text here
        a.row
          i home
          span Title
        a.row
          i home
          .max
            div Title
            label Some text here
        a.row
          img.circle.tiny(:src="'/beer-and-woman.jpg'")
          span Title
        a.row
          img.circle.tiny(:src="'/beer-and-woman.jpg'")
          .max
            div Title
            label Some text here
    button(data-ui="#dropdown6")
      span Video
      #dropdown6.dropdown.no-padding.small-width(data-ui="#dropdown6")
        video.responsive(autoplay, loop, muted, playsinline)
          source(:src="'/dance.mp4'", type="video/mp4")
</template>

<script setup lang="ts">
import domain from "./domain";
import data from "./data";
</script>
