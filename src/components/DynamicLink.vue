<template>
  <component :is="component"/>
</template>

<script>
export default {
  name: 'DynamicLink',
  data () {
    return {
      component: null,
    }
  },
  computed: {
    loader() {
      return () => import('@/components/HelloWorld');
    },
  },
  mounted() {
    this.loader()
      .then(() => {
        this.component = () => this.loader();
      })
      .catch(() => {
      });
  },
}
</script>
<style scoped>
</style>
