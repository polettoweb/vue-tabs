<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Item v-for="item in items" :key="item.id" @clicked="onClickChild" :ref="item.id" :item="item"/>
  </div>
</template>

<script>

export default {
  name: 'vue-tabs',
  components: {
    Item: () => import('./components/Item')
  },
  data() {
    return {
      ids: [],
      items: [
        {
          id: 1,
          title: "Title 1",
          content: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
        },
        {
          id: 2,
          title: "Title 2",
          content: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
        },
        {
          id: 3,
          title: "Title 3",
          content: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
        }

      ]
    }
  },
  methods: {
    listOfIds() {
      this.items.map( item => {
        return this.ids.push(item.id);
      })
    },
    onClickChild(value) {
      this.ids.map( item => {
        if (item === value) {
          return this.$refs[value][0]._data.active = ! this.$refs[value][0]._data.active
        } else {
          return this.$refs[item][0]._data.active = false
        }
      })
    }
  },
  mounted() {
    this.listOfIds();
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
