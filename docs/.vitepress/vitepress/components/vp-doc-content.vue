<template>
  <div class="doc-content-wrapper">
    <div class="doc-content-container">
      <Content
        ref="content"
        class="doc-content"
        @vnode-updated="updateDom"
        @vnode-mounted="updateDom"
      />
      <!-- <VpPageFooter /> -->
      <!-- <VPPageNav /> -->
    </div>
    <VPTableOfContent v-if="page.headers" />
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import { useData } from "vitepress";
import { insertTableWrapper } from '../utils';
// import VPPageFooter from './doc-content/vp-page-footer.vue';
import VPTableOfContent from "./doc-content/vp-table-of-content.vue";

const { page } = useData();
const content = ref<{ $el: HTMLElement }>();

const updateDom = () => {
  // insertLinkIcon();
  insertTableWrapper(content);
};
</script>