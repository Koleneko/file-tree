<template>
  <div>
    <div @click="nodeClicked" class="node" :style="{ 'margin-left': `${depth * 20}px` }">
      <icon :name="generateIconName()" />
      <h3>{{ node.name }}</h3>
      <icon v-if="(node.type === 'link' || node.type === 'file') && clicked" :name="'selected'" />
    </div>

    <div v-if="clicked">
      <FileTree v-for="child in node.contents" :key="child.name" :node="child" :depth="depth + 1" />
    </div>
  </div>
</template>

<script>
import Icon from './Icon.vue';

export default {
  name: 'FileTree',
  data() {
    return {
      clicked: false,
    };
  },
  props: {
    node: Object,
    depth: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    nodeClicked() {
      this.clicked = !this.clicked;
    },
    generateIconName() {
      switch (this.node.type) {
        case 'directory':
          return this.clicked ? 'directory-opened' : 'directory';
        case 'file':
          return 'file';
        case 'link':
          return 'link';
      }

      return;
    },
  },
  components: {
    Icon,
  },
};
</script>

<style scoped>
.node {
  display: flex;
  align-items: center;
  width: auto;
  height: auto;
  text-overflow: clip;
}
</style>
