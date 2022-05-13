<script>
import { reactive, ref } from "vue";
export default {
  name: "App",
  setup() {
    const data = reactive([
      { title: "计算机网络", type: "计算机", id: 1 },
      { title: "英语语法与写作", type: "外语", id: 2 },
      { title: "【刘琦考研英语长难句】每日一练", type: "考研", id: 3 },
      { title: "【刘琦考研英语长难句】每日二练", type: "考研", id: 4 },
      { title: "【刘琦考研英语长难句】每日三练", type: "考研", id: 4 },
    ]);
    const search = ref("");
    const filterData = ref(data);

    const handleSearch = () => {
      filterData.value = data.filter((item) => {
        return (
          item.title.includes(search.value) || item.type.includes(search.value)
        );
      });
    };
    return {
      data,
      search,
      handleSearch,
      filterData,
    };
  },
};
</script>

<template>
  <div>
    <div>
      <input type="text" v-model="search" />
      <button @click="handleSearch">search</button>
    </div>
    <ul>
      <li v-for="item in filterData" :key="item.id">
        {{ item.title }} - {{ item.type }}
      </li>
    </ul>
  </div>
</template>

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
