<template lang="pug">
#typography
  .large-space
  h4 Typography
  .medium-space
  h6.middle-align
    span Display and headline
    a.chip.circle(@click="domain.showSamples(data, '#display-headline h1, #display-headline h2, #display-headline h3, #display-headline h4, #display-headline h5, #display-headline h6', 'Display and headline', null, 'https://github.com/beercss/beercss/blob/main/docs/TYPOGRAPHY.md')")
      i code
  div
    label.radio
      input(type="radio", name="size-typography", @click="domain.updateSize('#display-headline *', 'small')")
      span small
    label.radio
      input(
        type="radio",
        name="size-typography",
        checked,
        @click="domain.updateSize('#display-headline *')"
      )
      span medium
    label.radio
      input(type="radio", name="size-typography", @click="domain.updateSize('#display-headline *', 'large')")
      span large
    .space
    #display-headline.wrap
      h1 Display
      h2 Display
      h3 Display
      h4 Headline
      h5 Headline
      h6 Headline
  .medium-space
  h6.middle-align
    span Formatting
    a.chip.circle(@click="domain.showSamples(data, '#formatting nav *', 'Formatting', null, 'https://github.com/beercss/beercss/blob/main/docs/BUTTON.md')")
      i code
  #formatting
    nav
      a.link link
      p.italic italic
      p.bold bold
      p.underline underline
      p.overline overline
      p.upper upper
      p.lower lower
      p.capitalize capitalize
      p.small-text small-text
      p.medium-text medium-text
      p.large-text large-text
</template>

<script setup lang="ts">
import domain from "./domain";
import data from "./data";
</script>
