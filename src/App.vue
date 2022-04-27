<template>
  <button @click="showImporter">Show Importer</button>
  <button @click="showCDNBasedImporter">Show CDN Based Importer</button>
  <!-- mount the component button -->
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import FuseImporter from "fuse-importer";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  methods: {
    showCDNBasedImporter() {
      const apiToken = "2DXqRB8ueCyqFkQwszyIVw";
      const templateId = "180";
      const FuseImporter = window.FuseImporter;
      const importer = new FuseImporter(apiToken, templateId, {
        env: "development",
      });

      importer.onSubmit = async (reviewedData) => {
        console.log({ reviewedData });
        return {
          errors: {},
          message: "Data imported successfully",
        };
      };

      const onValidateRecord = async () => {
        return {};
      };
      importer.onValidateRecord = onValidateRecord;

      importer.show();
    },
    showImporter() {
      const apiToken = "2DXqRB8ueCyqFkQwszyIVw";
      const templateId = "180";
      const importer = new FuseImporter(apiToken, templateId, {
        env: "development",
      });

      importer.onSubmit = async (reviewedData) => {
        console.log({ reviewedData });
        return {
          errors: {},
          message: "Data imported successfully",
        };
      };

      const onValidateRecord = async () => {
        return {};
      };
      importer.onValidateRecord = onValidateRecord;

      importer.show();
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
