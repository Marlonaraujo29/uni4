<template>
  <div class="app">
    <h1>Lista de Tarefas</h1>
    
    <div>     
      <input 
        v-model="newTask" 
        @keyup.enter="addTask" 
        type="text" 
        placeholder="Adicione uma tarefa"
      />
      <button @click="addTask">Adicionar</button>
    </div>
    
    
    <p v-if="tasks.length === 0">Nenhuma tarefa adicionada.</p>

    <ul>
      <li 
        v-for="(task, index) in tasks" 
        :key="index" 
        :class="{ completed: task.completed }"
      >
        <span @click="toggleTask(index)">{{ task.name }}</span>
        <button class="remove-btn" @click="removeTask(index)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', 
      tasks: [],   
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ name: this.newTask.trim(), completed: false });
        this.newTask = '';
      }
    },
   
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
  mounted() {
    console.log('Seu componente foi montado!');
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
}

.app {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 300px;
  margin: 50px auto;
  text-align: center;
}

input {
  width: calc(100% - 60px);
  padding: 8px;
  margin-right: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  padding: 8px 12px;
  background: #28a745;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 2%;
  
}

button:hover {
  background: #218838;
}

ul {
  list-style: none;
  padding: 0;
  margin: 20px 0 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

li span {
  cursor: pointer;
}

li.completed span {
  text-decoration: line-through;
  color: gray;
}

.remove-btn {
  background: #dc358b;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  cursor: pointer;
}

.remove-btn:hover {
  background: #58193a;
}
</style>