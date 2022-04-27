<template>
  <!-- <button @click="showImporter">Import</button> -->
  <!-- mount the component button -->
  <button @click="mountRC">mount rc</button>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import { DateTime } from "luxon";
// import FuseImporter from "fuse-importer";
import React from "react";
import { createRoot } from "react-dom/client";

// var sleep = (n) => new Promise((resolve) => setTimeout(resolve, n));
// const importer = new FuseImporter("2DXqRB8ueCyqFkQwszyIVw", "180", {
//   env: "development",
// });

// importer.onSubmit = async (reviewedData) => {
//   // simulate api call delay
//   await sleep(2000);
//   console.log({ reviewedData });

//   // simulate random errors on submitted data
//   const validationErrors = {};
//   const maxErrorCount = 6;

//   const errorCount = Math.round(
//     Math.random() * Math.min(reviewedData.length, maxErrorCount)
//   );
//   for (let i = 0; i < errorCount; i++) {
//     const errorIndex = Math.round(Math.random() * reviewedData.length);
//     if (errorIndex < reviewedData.length) {
//       const recordFields = Object.keys(reviewedData[0]).filter(
//         (r) => r !== "_meta"
//       );
//       const fieldWithErrorIndex = Math.floor(
//         Math.random() * recordFields.length
//       );
//       validationErrors[reviewedData[errorIndex]._meta.id] = {
//         [recordFields[fieldWithErrorIndex]]: "Duplicate value",
//       };
//     }
//   }

//   let message = null;
//   if (!Object.keys(validationErrors).length)
//     message = "Data imported successfully";
//   else message = "Invalid records identified when importing to database";

//   return {
//     message,
//     errors: validationErrors,
//   };
// };

// const onValidateRecord = async () => {
//   const errors = {};
//   return errors;
// };

// importer.onValidateRecord = onValidateRecord;

const res = DateTime.now()
  .setZone("America/New_York")
  .minus({ weeks: 1 })
  .endOf("day")
  .toISO();
console.log({ res });

const TestComponent = () => {
  return /*#__PURE__*/ React.createElement("div", null, "testing firme");
};

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  methods: {
    // showImporter() {
    //   importer.show();
    // },
    mountRC() {
      const div = document.createElement("div");
      div.setAttribute("id", "idtest");
      div.innerHTML = "test";
      document.body.appendChild(div);

      const container = document.getElementById("idtest");
      const root = createRoot(container);
      root.render(
        React.createElement(TestComponent, {
          test: "test",
        })
      );

      // ReactDOM.createRoot(
      //   React.createElement(TestComponent, {
      //     test: "test",
      //   }),
      //   document.getElementById("idtest")
      // );
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
