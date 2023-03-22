<template>
  <div class="container">
    <div class="card mt-3 px-3">
      <div class="row col-5 py-3" style="min-width: 290px">
        <form action="" class="">
          <input
            type="text"
            class="form-control"
            placeholder="Nome da Lista"
            maxlength="35"
            v-model="input_nome"
            id="nome"
          />
        </form>
      </div>
      <div class="row pb-3">
        <form action="" class="col-7">
          <input
            type="text"
            class="form-control"
            placeholder="Item"
            v-model="input_item"
          />
        </form>
        <form action="" class="col-3">
          <input
            type="number"
            class="form-control"
            placeholder="Quantidade"
            min="1"
            v-model="input_quantia"
          />
        </form>
        <form action="" class="col-2">
          <button class="btn btn-md btn-warning" @click="check_item($event)">
            +
          </button>
        </form>
      </div>
      <div class="row">
        <div class="col-12">
          <table class="table table-bordered" id="tableId">
            <thead class="table">
              <tr>
                <th class="col-1 text-center">#</th>
                <th class="col-9">Item</th>
                <th class="col-2">Quantidade</th>
              </tr>
            </thead>
            <tbody
              class="table preview"
              id="tableBody"
              v-show="body_id"
            ></tbody>
          </table>
        </div>
      </div>
      <div class="col-12 text-center my-2">
        <input
          type="submit"
          class="btn btn-success my-3"
          value="Confirmar"
          id="submit"
          @click="submit($event)"
        />
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Form",

  data() {
    return {
      nome: "",
      itens: [],
      quantias: [],
      itemName: "",
      quantia: "",
      input_nome: "",
      input_item: "",
      input_quantia: "",
      row_id: "",
      body_id: 0,
    };
  },

  methods: {
    check_item(e) {
      e.preventDefault();

      //contagem de itens no tbody

      let row_id =
        document.getElementById("tableId").tBodies[0].rows.length + 1;

      this.itemName = this.input_item;
      let itemName = this.itemName;

      this.quantia = this.input_quantia;
      let quantia = this.quantia;

      //quantia minima = 1

      if (quantia == undefined || quantia == "" || quantia == null) {
        quantia = 1;
      }

      //verificar se o item é nulo

      if (itemName == undefined || itemName == "" || itemName == null) {
        alert("Preencher Item!");
        return false;
      } else {

        alert("Adicionado " + quantia + " unidade(s) de " + itemName + "!");

        //inclusão de nova linha

        let table = document.getElementById("tableBody");
        let row = document.createElement("tr");
        /*let c1 = document.createElement("td");*/
        let c2 = document.createElement("td");
        let c3 = document.createElement("input");

        /*c1.innerHTML = "-";
        c1.id = `row_id_${row_id}`;
        c1.className = "border-0";
        c1.value = row_id;*/

        c2.innerText = itemName;
        c2.id = `itemName_${row_id}`;
        c2.className = "itemName border-0";
        c2.value = itemName;

        c3.className = "quantia form-control";
        c3.type = "number";
        c3.id = `quantia_${row_id}`;
        c3.min = 1;
        c3.value = quantia;

        let btn = document.createElement("button");
        btn.className = "btn btn-link text-danger w-100";
        btn.style = "text-decoration:none";
        btn.type = "submit";
        btn.innerText = "X";

        table.append(row);
        row.insertCell(0).appendChild(btn);
        row.insertCell(1).appendChild(c2);
        row.insertCell(2).appendChild(c3);

        btn.onclick = function (event) {
          event.target.closest("tr").remove();

          this.row_id = row_id - 1;
        };

        //reset de input + abertura de tbody
        this.input_item = "";
        this.input_quantia = "";
        this.body_id = 1;
      }
    },

    async submit(e) {

      this.nome = this.input_nome;
      let nome = this.nome;

      let row_id = document.getElementById("tableId").tBodies[0].rows.length;

      //condição para envio
      if (nome == "") {
        alert("Nomear Lista!");
        return false;
      }

      if (row_id <= 0) {
        alert("Lista Vazia!");
        return false;
      }

      //array de elementos (itens e quantidades)
      let itemArray = [];

      let itemName = document.getElementsByClassName("itemName");
      for (let list of itemName) {
        itemArray.push(list.value);
      }

      let quantiaArray = [];

      let quantia = document.getElementsByClassName("quantia");
      for (let list of quantia) {
        quantiaArray.push(list.value);
      }


      //Envio para JSON?
      /*e.preventDefault();

      const data = {
        nome: this.nome,
        numero: row_id,
        itens: itemArray,
        quantias: quantiaArray,
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/listas", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      console.log(res);*/

      //mensagem de sucesso
      alert("Lista " + nome + " criada!");

      //log da lista finalizada
      console.log(nome, row_id, itemArray, quantiaArray);
    },
  },

  mounted() {
    let body_id = this.body_id;
    if (body_id <= 0) {
      this.body_id = false;
    }
  },
};
</script>

<style scoped>
</style>