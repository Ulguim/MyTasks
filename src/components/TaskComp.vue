<template>
  <div id="task">
    <h3>Minhas Tarefas</h3>

    <form @submit.prevent="addTask">
      <div class="formFields">
        <input
          class="inputField"
          v-model="task"
          type="text"
          placeholder="Exercício"
        />
        <button class="submitButton" type="submit">Adicionar</button>
      </div>
    </form>
    <ItemList
      :finish="finishTask"
      :delete="deleteTask"
      :lista="tasks"
    ></ItemList>
  </div>
</template>
''

<script>
import ItemList from "./ItemList.vue";

export default {
  name: "TaskComp",
  components: { ItemList },
  data() {
    let data = [];
    if (localStorage.getItem("MyTasks") != null) {
      data = JSON.parse(localStorage.getItem("MyTasks"));
    }
    return {
      task: "",
      msg: "Bem Vindo: ",
      tasks: data || [],
    };
  },
  methods: {
    addTask() {
      this.task != ""
        ? this.tasks.push({ name: this.task, id: Date.now(), done: false })
        : alert("Digite uma tarefa");
      this.task = "";
      localStorage.setItem("MyTasks", JSON.stringify(this.tasks));
    },
    deleteTask(key) {
      this.tasks = this.tasks.filter((item) => item.id != key);
      localStorage.setItem("MyTasks", JSON.stringify(this.tasks));
    },
    finishTask(key) {
      this.tasks.map((item) => {
        if (item.id == key) {
          item.done = !item.done;
        }
      });
    },
  },
};
</script>

<style scoped>
#task {
  display: flex;
  width: 100%;
  margin-bottom: 10px;
  width: 100%;
  flex-direction: column;
}

.inputField {
  width: 500px;
  height: 50px;
  max-width: 500px;
  border: none;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  color: gray.300;
  border-radius: 5px;
}

.submitButton {
  background-color: #4caf50;
  border: none;
  color: white;
  width: 500px;
  border-radius: 5px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
  height: 50px;
  margin: 4px 2px;
  cursor: pointer;
}
.formFields {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>
