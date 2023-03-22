<template>
    <div class="container">
        <table class="table table-hover">
        <thead class="table">
            <tr>
                <th class="col-1">#</th>
                <th class="col-9">Item</th>
                <th class="col-2 remover">Quantidade</th>
            </tr>
        </thead>
        <tbody class="table preview" id="tableBody">
            <tr class="table_row">
                <td>{{ row_id }}</td>
                <td>{{ item }}</td>
                <td class="remover" id="quantia">
                    <div class="input-group input-group-sm"> 
                        <input type="number" min="1" class="form-control" id="quantia" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-sm" :value='quantia'>
                        <button class="btn btn-danger input-group-number" id="inputGroup-sizing-sm" @click="excluir($event)">X</button>
                    </div>
                </td>
            </tr>
        </tbody>
        </table>
    </div>
</template>

<script>

export default {
    name:'Preview',
    methods:{
        excluir(e){
            e.preventDefault()
            document.getElementById("tableBody").deleteRow(0);
        },
    },
    data(){
        
    },
    props:{
        item: Object,
        quantia: Object,
        row_id: Boolean,
    },

    emits: 'myTable',
}

</script>

<style scoped>

.container{
    box-sizing: border-box;
}

.remover{
    width: 100%;
    text-align: center;
    min-width: 100px;
}

.table_row{
    line-height: 300%;
}

</style>