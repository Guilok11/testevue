<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <form id="burger-form" @submit="createBurger">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome" required>
      </div>
      <div class="input-container">
        <label for="pao">Escolha o pão:</label>
        <select name="pao" id="pao" v-model="pao" required>
          <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
        </select>
        <span v-show="!pao" class="error-message"></span>
      </div>
      <div class="input-container">
        <label for="carne">Escolha a carne do seu Lanche:</label>
        <select name="carne" id="carne" v-model="carne" required>
          <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
        </select>
        <span v-show="!carne" class="error-message"></span>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
        <span v-show="!hasSelectedOpcionais" class="error-message"></span>
      </div>
      <div class="input-container">
        <input class="submit-btn" type="submit" value="Criar meu Lanche!">
      </div>
    </form>
  </div>
</template>

<script>
import Message from './Message.vue';

export default {
  name: "BurgerForm",

  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null
    }
  },

  computed: {
    hasSelectedOpcionais() {
      return this.opcionais.length > 0;
    }
  },

  methods: {
    async getIngredientes() {
      const req = await fetch('http://localhost:3000/ingredientes');
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
    },

    async createBurger(e){
      e.preventDefault();

      if (!this.nome) {
        this.msg = "Insira o nome do cliente.";
        return;
      }

      if (!this.pao) {
        this.msg = "Selecione o tipo de pão.";
        return;
      }

      if (!this.carne) {
        this.msg = "Selecione o tipo de carne.";
        return;
      }

      if (!this.hasSelectedOpcionais) {
        this.msg = "Selecione pelo menos um opcional.";
        return;
      }

      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: {"Content-Type": "application/json"},
        body: dataJson
      });

      const res = await req.json();
      this.msg = `Pedido N° ${res.id} realizado com sucesso`;

      setTimeout(() => (this.msg = ""), 3000);

      // Limpar os campos do formulário após a criação do lanche
      this.nome = "";
      this.pao = "";
      this.carne = "";
      this.opcionais = [];
    }
  },

  mounted () {
    this.getIngredientes();
  },

  components: {
    Message
  }
}
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #111;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#opcionais-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
}

.submit-btn {
  background-color: #111;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #111;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  background-color: transparent;
  color: #111;
}


</style>
