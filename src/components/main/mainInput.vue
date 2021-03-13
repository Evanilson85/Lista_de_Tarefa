<template>
  <main>
    <section class="section">
      <div>
        <h1>Digite a sua tarefa</h1>
        <h2
          v-if="
            tarefas.length > 1
              ? (textTarefa = 'Tarefas')
              : (textTarefa = 'Tarefa')
          "
        >
          {{ tarefas.length }} {{ textTarefa }}
        </h2>
      </div>
      <hr />
      <div class="input">
        <input
          type="text"
          name=""
          placeholder="Digite a sua tarefa"
          id=""
          :class="erro ? 'error' : ' '"
          v-model="valueTarefas"
        />
        <!-- @change="teste($event)" -->
        <h3 v-if="erro">Digite alguma tarefa</h3>
        <button @click="salve" class="salve">s</button>
      </div>

      <ul v-if="tarefas.length > 0">
        <li v-for="(tarefa, index) in tarefas" :key="index" :id="index">
          <div>
            <input
              type="checkbox"
              ref="inputLabel"
              class="check"
              checked
              :id="'check' + index"
              hidden
            />
            <label
              ref="label"
              :for="'check' + index"
              @click="cancel($event)"
              :class="list ? 'risc' : ' '"
              >{{ tarefa }}
            </label>
          </div>

          <div>
            <button @click="excluir(index)" class="btnDelete">x</button>
          </div>
        </li>
      </ul>

      <div v-else>
        <h1 class="null">Não tem tarefa</h1>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      textTarefa: "",
      list: "",
      erro: false,
      valueTarefas: "",
      tarefas: [],
    };
  },
  methods: {
    salve() {
      let valor = this.valueTarefas;

      if (valor.length > 0) {
        this.tarefas.push(valor);
        this.erro = false;
      } else {
        this.erro = true;
      }

      return (this.valueTarefas = "");
    },

    excluir(index) {
      this.tarefas.splice(index, 1);
    },
    cancel(e) {
      let atual = e.target;
      let check = atual.parentElement.children[1];

      console.log();
      console.log(check);
      if (check) {
        check.classList.toggle("risc");
      }
    },
  },
};
</script>

<style scoped>
main {
  width: 100%;
  height: auto;
}
.section {
  width: 90%;
  background-color: #fff;
  margin: 0 auto;
  position: relative;
  top: -35px;
  min-height: 550px;
  border-radius: 15px;
}
.section hr {
  width: 90%;
  margin: 0 auto;
  height: 2px;
  background-color: #aa591b;
  border: none;
}
h1 {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  padding: 15px;
}
h2 {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  padding: 15px;
}
h3 {
  color: red;
  margin: 10px;
  transition: 0.2s linear;
}
.input {
  width: 90%;
  margin: 20px auto;
  position: relative;
}
.input input {
  width: 100%;
  height: 55px;
  border-radius: 9px;
  border: none;
  box-shadow: 4px 5px 14px 0px #aa591b;
  padding: 12px;
}
.input .salve {
  height: 40px;
  width: 40px;
  border-radius: 18%;
  border: none;
  background-color: #52d837;
  font-size: 30px;
  color: #fff;
  cursor: pointer;
  position: absolute;
  right: 10px;
  top: 8px;
}

.error {
  border: 1px solid red !important;
  box-shadow: 4px 5px 14px 0px #f10b0b !important;
}

.section ul {
  width: 85%;
  margin: 0 auto;
  height: auto;
  padding: 1px;
}
.section ul li {
  display: flex;
  align-items: center;
  width: 100%;
  height: 55px;
  border-radius: 9px;
  border: none;
  box-shadow: 4px 5px 14px 0px #42403b;
  padding: 12px;
  justify-content: space-between;
  margin: 35px 0;
}
.section ul li label {
  font-size: 20px;
  font-family: arial;
  margin: 0 10px;
  cursor: pointer;
}

.section ul li .check {
  cursor: pointer;
}

.section ul li .btnDelete {
  height: 40px;
  width: 40px;
  border-radius: 18%;
  border: none;
  background-color: #d83737;
  font-size: 30px;
  color: #fff;
  cursor: pointer;
}
.section ul li .btnDelete:hover {
  background-color: #977a7a;
}
.risc {
  text-decoration: line-through;
  color: #999;
  cursor: not-allowed;
}
.null {
  color: #aa591b;
}
@media (min-width: 769px) {
  .section {
    max-width: 560px;
    background-color: #fff;
    margin: 0 auto;
  }
}
</style>