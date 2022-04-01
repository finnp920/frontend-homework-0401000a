<template>
  <div class="area-work">
    <div class="page-top">
      <h3 class="pathname">{{ pagePathName }}</h3>
      <div class="button-wrap">
        <button style="width: auto; padding: 0 10px; background-color: #ffffff; font-size: 18px" @click="setNumOfColumns(1)">↻</button>
        <button @click="setNumOfColumns(2)">2</button>
        <button @click="setNumOfColumns(3)">3</button>
        <button @click="setNumOfColumns(4)">4</button>
      </div>
    </div>
    <div class="box-wrap" :style="{ gridTemplateColumns: `repeat(${numOfColumns}, 1fr)` }">
      <div v-for="(item, idx) in box.items" :key="`box${idx}`" class="box">
        <p>{{ item.name }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import { mapGetters, mapMutations } from 'vuex';
import 'scss/pages/work.scss';

export default {
  name: 'Work',
  props: {
    box: {
      type: Object,
      default() {
        return this.$store.state.ui.box;
      },
    },
  },
  data() {
    return {};
  },
  computed: {
    ...mapGetters({
      numOfColumns: 'ui/getNumOfColumns',
    }),
    pagePathName() {
      return `page path: ${this.$route.path}`;
    },
  },
  methods: {
    ...mapMutations({ setNumOfColumns: 'ui/setNumOfColumns' }),
  },
};
</script>

<style lang="scss" scoped>
.box-wrap {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0 8px;
}
</style>
