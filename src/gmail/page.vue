<template lang="pug">
div
  nav.left.no-space.m.l
    .large-space
    .medium-space
    a.button.fill.square.round.extra(data-ui="#modal-add")
      i add
    .space
    a(href="/gmail", :class="{ active: data.url == '/gmail' }")
      i inbox
      .tooltip.right Inbox
    a(href="/gmail/snoozed", :class="{ active: data.url == '/gmail/snoozed' }")
      i watch_later
      .tooltip.right Snoozed
    a(
      href="/gmail/important",
      :class="{ active: data.url == '/gmail/important' }"
    )
      i label_important
      .tooltip.right Important
    a(href="/gmail/sent", :class="{ active: data.url == '/gmail/sent' }")
      i send
      .tooltip.right Sent
    a(href="/gmail/drafts", :class="{ active: data.url == '/gmail/drafts' }")
      i insert_drive_file
      .tooltip.right Drafts
    a(href="/gmail/spam", :class="{ active: data.url == '/gmail/spam' }")
      i error_outline
      .tooltip.right Spam
    a(data-ui="#themes1")
      i brightness_medium
      .tooltip.right Themes
    themes(id="themes1", v-model="data")
      .large-space
      .medium-space

  nav.right.m.l
    .medium-space
    .space
    button.circle.transparent.large
      span.tooltip.left Calendar
      img.no-round(:src="'/calendar.png'")
    button.circle.transparent.large
      span.tooltip.left Keep
      img.no-round(:src="'/keep.png'")
    button.circle.transparent.large
      span.tooltip.left Tasks
      img.no-round(:src="'/tasks.png'")
    button.circle.transparent.large
      span.tooltip.left Contacts
      img.no-round(:src="'/contacts.png'")

  nav.bottom.s
    a(href="/gmail", :class="{ active: data.url == '/gmail' }")
      i inbox
      div Inbox
    a(href="/gmail/sent", :class="{ active: data.url == '/gmail/sent' }")
      i send
      div Sent
    a.button.fill.square.round.extra(data-ui="#modal-add-small")
      i add
    a(href="/gmail/drafts", :class="{ active: data.url == '/gmail/drafts' }")
      i insert_drive_file
      div Drafts
    a(data-ui="#themes2")
      i brightness_medium
      div Theme
    themes(id="themes2", v-model="data")
      .large-space
      .medium-space

  nav.top
    button.circle.large.small-margin.transparent(data-ui="#dropdown-menu")
      i menu
      #dropdown-menu.dropdown.no-wrap(data-ui="#dropdown-menu")
        a.row(href="/gmail")
          i inbox
          .max Inbox
        a.row(href="/gmail/snoozed")
          i watch_later
          .max Snoozed
        a.row(href="/gmail/important")
          i label_important
          .max Important
        a.row(href="/gmail/sent")
          i send
          .max Sent
        a.row(href="/gmail/drafts")
          i insert_drive_file
          .max Drafts
        a.row(href="/gmail/spam")
          i error_outline
          .max Spam
        a.row(data-ui="#themes3")
          i brightness_medium
          .max Themes
    img(v-show="!data.isDark", :src="'/gmail-light.png'")
    img(v-show="data.isDark", :src="'/gmail-dark.png'")
    .max
    .max.field.round.suffix.prefix.small.no-margin.m.l.white.black-text
      i.front search
      input(type="text", data-ui="#dropdown-search")
      i.front mic
    .max
    button.circle.large.transparent.s(data-ui="#modal-search")
      i search
    button.circle.large.transparent.m.l(data-ui="#dropdown-settings")
      i settings
      #dropdown-settings.dropdown.left.no-wrap(
        data-ui="#dropdown-settings"
      )
        a
          div Account
          label Change account
        a
          div Appearance
          label Change display settings
    button.circle.large.transparent.m.l(data-ui="#dropdown-apps")
      i apps
      #dropdown-apps.dropdown.left.padding.no-wrap(data-ui="#dropdown-apps")
        .grid.no-space
          .s4.center-align
            button.transparent.circle.large
              img.no-round(:src="'/calendar.png'")
          .s4.center-align
            button.transparent.circle.large
              img.no-round(:src="'/keep.png'")
          .s4.center-align
            button.transparent.circle.large
              img.no-round(:src="'/tasks.png'")
          .s4.center-align
            button.transparent.circle.large
              img.no-round(:src="'/contacts.png'")
          .s4.center-align
            button.transparent.circle.large
              img.no-round(:src="'/favicon.png'")
    button.circle.large.small-margin.transparent(@click="redirect('/')")
      img.responsive(:src="'/favicon.png'")
    themes(id="themes3", v-model="data")

  main.responsive.max
    #modal-add.modal.round.large-width
      nav
        button.circle.transparent(data-ui="#modal-add")
          i arrow_back
        h5 New message
        .max
        button.circle.transparent(data-ui="#modal-add")
          i attach_file
        button.circle.transparent(data-ui="#modal-add")
          i send
      .grid
        .s12
          .field.label.border
            input(type="text")
            label From
        .s12
          .field.label.border
            input(type="text")
            label To
        .s12
          .field.label.border
            input(type="text")
            label Subject
        .s12
          .field.label.border.textarea
            textarea
            label Message

    #modal-add-small.modal.top-round.bottom
      nav
        button.circle.transparent(data-ui="#modal-add-small")
          i arrow_back
        h5 New message
        .max
        button.circle.transparent(data-ui="#modal-add-small")
          i attach_file
        button.circle.transparent(data-ui="#modal-add-small")
          i send
      .grid
        .s12
          .field.label.border
            input(type="text")
            label From
        .s12
          .field.label.border
            input(type="text")
            label To
        .s12
          .field.label.border
            input(type="text")
            label Subject
        .s12
          .field.label.border.textarea
            textarea
            label Message

    #modal-search.modal.top.transparent
      nav
        .max.m.l
        .max.field.round.suffix.prefix.small.no-margin.white.black-text
          i.front search
          input(type="text")
          i.front mic
        .max.m.l

    home(v-if="data.url == '/gmail'")
    drafts(v-if="data.url == '/gmail/drafts'")
    important(v-if="data.url == '/gmail/important'")
    sent(v-if="data.url == '/gmail/sent'")
    snoozed(v-if="data.url == '/gmail/snoozed'")
    spam(v-if="data.url == '/gmail/spam'")
</template>

<script setup lang="ts">
import { onMounted } from "vue";
import themes from "../shared/themes.vue";
import data from "./data";
import sharedDomain from "../shared/domain";
import home from "./home.vue";
import drafts from "./drafts.vue";
import important from "./important.vue";
import sent from "./sent.vue";
import snoozed from "./snoozed.vue";
import spam from "./spam.vue";
import { onRoute, redirect } from "../shared/router";

onMounted(() => {
  sharedDomain.initTheme(data.value);
});

onRoute((url:string) => {
  data.value.check = false;
  data.value.url = url;
});
</script>
