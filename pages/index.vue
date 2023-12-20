<template>
  <div>
    {{ tasks }}
  </div>
</template>

<script>
import axios from "@/static/axios.js";
export default {
  name: "IndexPage",
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async GET_DATA(path) {
      response = await axios.get(path);
      return response.data;
    },
  },
  mounted() {
    this.$nextTick(async () => {
      let self = this;
      await Promise.all([this.GET_DATA("task")]).then((val) => {
        self.tasks = val[0];
      });
    });
  },
};
</script>
