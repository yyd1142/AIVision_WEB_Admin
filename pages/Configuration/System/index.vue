<template>
  <div>
    <RootPage :language="language" default-active="1-2" :default-openeds="['1']">
      <div class="System" slot="page">

      </div>
    </RootPage>
  </div>
</template>

<script>
  import RootPage from "@pages/index.vue";
  import {TitleCell, MyFormCell, DataDetailCell, DataDetailTitle} from "@components";

  export default {
    name: "System",
    components: {
      RootPage,
      TitleCell,
      MyFormCell,
      DataDetailCell,
      DataDetailTitle
    },
    computed: {
      languageDatas() {
        return this.$store.getters.languageDatas;
      },
    },
    async asyncData(ctx) {
      const language = ctx.query.language || 'en';
      return {
        language: language,
      }
    },
    mounted() {

    },
    methods: {

    }
  }
</script>

<style lang="less">
  .System {
    width: 100%;
    display: flex;
    display: -webkit-flex; /* Safari */
    padding: 0 15px 30px 15px;
    flex-direction: column;
    .my-box-shadow {
      -moz-box-shadow: 0px 1px 5px #ccc; /* 老的 Firefox */
      box-shadow: 0px 1px 5px #ccc;
    }

  }
</style>
