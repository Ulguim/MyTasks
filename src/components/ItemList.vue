<template>
  <div id="#itemList">
    <div class="listBox">
      <div :key="item.id" v-for="item in lista" class="itemBox">
        <text
          style="
            font-size: 16px;
            color: black;
            margin-inline: 20px;
            margin-right: auto;
            text-align: start;
          "
        >
          {{ item.name }}</text
        >
        <button @click="deleteItem(item.id)" class="DeleteButton">
          Deletar
        </button>
        <button v-show="!item.done" @click="finishItem(item.id)" class="button">
          Concluir
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "itemList",
  data() {
    return {};
  },
  props: ["lista", "delete", "finish"],
  methods: {
    deleteItem(key) {
      this.delete(key);
    },
    finishItem(key) {
      this.finish(key);
    },
  },
};
</script>

<style scoped>
#itemList {
  min-width: 280px;
  width: 500px;
  max-height: 400px;
}
.listBox {
  padding-top: 20px;
  display: flex;
  flex-direction: column;

  width: 100%;
  gap: 20px;
  min-width: 280px;
  overflow-y: scroll;
  overflow-x: hidden;
  max-height: 500px;
  min-height: 500px;
  background-color: #f5f5f5;
  border-radius: 5px;

  align-items: top;
}

.listBox::-webkit-scrollbar {
  width: 5px;
}

.listBox::-webkit-scrollbar-track {
  border-radius: 10px;
}

.listBox::-webkit-scrollbar-thumb {
  background: #4caf50;
  border-radius: 10px;
}

.listBox::-webkit-scrollbar-thumb:hover {
  background: #4caf50;
}
.listData {
  min-width: 50px;
  min-height: 20px;
  list-style-type: none;
}

.button {
  background-color: #4caf50;
  border: none;
  color: white;
  width: 150px;
  border-radius: 5px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
  margin-right: 20px;
  margin-left: 10px;
  height: 25px;
  padding-left: 10px;
}

.DeleteButton {
  background-color: red;
  border: none;
  color: white;
  width: 150px;
  border-radius: 5px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
  height: 25px;
  margin-right: 5px;
}

.itemBox {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  height: 50px;
  min-height: 50px;
  margin-left: 10px;
  margin-right: 10px;
  background-color: white;
  border-radius: 5px;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
</style>
