<template>
  <div class="gnb-item" :depth="depth">
    <!-- you may make use of this component to draw gnb items -->
    <span v-if="!pathname">{{ name }}</span>
    <span v-else class="link">
      <router-link :to="pathname">{{ name }}</router-link>
    </span>
    <template v-if="depth < 4 && children.length > 0">
      <GnbItem
        v-for="(item, index) in children"
        :key="`item-${depth + 1}-${index}`"
        :name="item.name"
        :pathname="item.pathname"
        :children="item.children"
        :depth="depth + 1"
      />
    </template>
  </div>
</template>

<script>
export default {
  name: 'GnbItem',
  props: {
    name: {
      type: String,
      required: true,
    },
    pathname: {
      type: String,
      default: '',
    },
    children: {
      type: Array,
      default: () => [],
    },
    depth: {
      type: Number,
      default: 1,
    },
  },
};
</script>
