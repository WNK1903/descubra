<template>

  <div id="top">
    {{top}}
  </div>
  <div id="middle">
    {{middle}}
  </div>
  <div id="bottom">
    {{bottom}}
  </div>

</template>

<script>
export default {
  name: "Game",
  data: function () {
    return {
      top: 'Topo',
      middle: 'Meio',
      bottom: 'Bottom'
    };
  },
  mounted() {},
  methods: {},
};
</script>

<style scoped>
#top{
  height: 10vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#middle{
  height: 60vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#bottom{
  height: 30vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
