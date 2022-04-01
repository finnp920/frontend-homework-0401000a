<template>
  <div class="dashboard-wrap">
    <header />
    <div class="dashboard">
      <gnb :list="gnbList" />
      <router-view name="area" />
    </div>
  </div>
</template>
<script>
import 'scss/layouts/dashboard.scss';

export default {
  name: 'DashboardLayout',
  data() {
    return {
      gnbList: [],
    };
  },
  created() {
    this.getGnb();
  },
  methods: {
    async getGnb() {
      const res = await this.API.getGnb();
      if (!res) return;
      this.gnbList = res.data;
    },
  },
};
</script>
