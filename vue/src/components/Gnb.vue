<template>
  <div id="gnb">
    <h3 class="gnb-title">Sample</h3>
    <div class="gnb-inner">
      <div class="gnb-item" depth="1">
        <span>Menu 1</span>
        <div class="gnb-item" depth="2">
          <span class="link">
            <router-link to="/1-1">Menu 1-1</router-link>
          </span>
        </div>
        <div class="gnb-item" depth="2">
          <span>Menu 1-2</span>
          <div class="gnb-item" depth="3">
            <span class="link">
              <router-link to="/1-2-1">Menu 1-2-1</router-link>
            </span>
          </div>
        </div>
      </div>
      <div class="gnb-item" depth="1">
        <span class="link">
          <router-link to="/2">Menu 2</router-link>
        </span>
      </div>
    </div>
    <h3 class="gnb-title">API menu</h3>
    <div class="gnb-inner">
      <!-- your code goes from here -->
      <GnbItem v-for="(item, index) in items" :key="`item-${index}`" :name="item.name" :pathname="item.pathname" :children="item.children" />
    </div>
  </div>
</template>
<script>
import 'scss/components/gnb.scss';
import GnbItem from './GnbItem.vue';

export default {
  components: { GnbItem },
  name: 'Gnb',
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      sampleItems: [
        {
          name: 'Menu 1',
          children: [
            {
              name: 'Menu 1-1',
              pathname: '/1-1',
            },
            {
              name: 'Menu 1-2',
              children: [
                {
                  name: 'Menu 1-2-1',
                  pathname: '/1-2-1',
                },
              ],
            },
          ],
        },
        {
          name: 'Menu 2',
          pathname: '/2',
        },
      ],
      items: this.list,
    };
  },
  watch: {
    list(value) {
      if (!Array.isArray(value)) return;
      this.items = value;
    },
  },
};
</script>
