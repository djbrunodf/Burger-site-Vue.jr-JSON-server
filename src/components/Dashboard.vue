<template>
    <div class="table-box">
        <Message :msg="msg" v-show="msg" />
        <div class="table-row table-head">
            <div class="table-cell-number">
                <p>#:</p>
            </div>
            <div class="table-cell">
                <p>Cliente:</p>
            </div>
            <div class="table-cell">
                <p>Pão:</p>
            </div>
            <div class="table-cell">
                <p>Carne:</p>
            </div>
            <div class="table-cell">
                <p>Opcionais:</p>
            </div>
            <div class="table-cell">
                <p>Ações:</p>
            </div>
        </div>
        <div class="table-row" v-for="burger in burgers" :key="burger.id">
            <div class="table-cell-number">
                <p>{{ burger.id }}</p>
            </div>
            <div class="table-cell">
                <p>{{ burger.nome }}</p>
            </div>
            <div class="table-cell">
                <p>{{ burger.pao }}</p>
            </div>
            <div class="table-cell">
                <p>{{ burger.carne }}</p>
            </div>
            <div class="table-cell">
                <ul>
                    <li v-for="(opcional, index) in burger.opcionais" :key="index">
                        {{ opcional }}
                    </li>
                </ul>
            </div>
            <div class="table-cell">
                <select name="status" class="status" @change="updateBurger($event, burger.id)">
                    <option value="">Selecione</option>
                    <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">
                        {{ s.tipo }}
                    </option>
                </select>
                <button class="delete-btn" @click.prevent="deleteBurger(burger.id)">Cancelar</button>
            </div>
        </div>
    </div>
</template>

<script>
import Message from './Message.vue';

    export default {
        name: "Dashboard",
        components: { 
            Message
        },
        data() {
            return {
                burgers: null,
                burger_id: null,
                status: [],
                msg: null, 
            }
        },
        methods: {
            async getPedidos() {

                const req = await fetch("http://localhost:3000/burgers");

                const data = await req.json();

                this.burgers = data;

                this.getStatus();

            },
            async getStatus() {
                const req = await fetch("http://localhost:3000/status");

                const data = await req.json();

                this.status = data;
            },
            async deleteBurger(id) {
                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "DELETE"
                });

                const res = await req.json();

                this.msg = `Pedido Removido com Sucesso`;
  
                setTimeout(() => this.msg = "", 3000);

                this.getPedidos();

            },
            async updateBurger(event, id) {

                const option = event.target.value;

                const dataJson = JSON.stringify({ status: option })

                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "PATCH",
                    headers: { "Content-Type": "application/json" },
                    body: dataJson
                });

                const res = await req.json();

                this.msg = `O Pedido N° ${ res.id } Foi Atualizado Para ${ res.status }`;
  
                setTimeout(() => this.msg = "", 3000);

            }
        },
        mounted() {
            this.getPedidos();
        }
    }

</script>

<style scoped>

    .table-box {
        margin: 50px auto;
    }

    .table-row {
        display: table;
        width: 80%;
        margin: 10px auto;
        background: transparent;
        padding: 12px 0;
        box-shadow: 0 1px 4px 0 rgba(0, 0, 50, 0.3);
        
    }

    .table-cell {
        display: table-cell;
        width: 19%;
        text-align: center;
        padding: 4px 0;
        border-right: 1px solid #d6d4d4;
        vertical-align: middle;
    }

    .table-cell-number {
        display: table-cell;
        width: 5%;
        text-align: center;
        padding: 4px 0;
        border-right: 1px solid #d6d4d4;
        vertical-align: middle;
    }


    select {
        padding: 12px 6px;
        margin-right: 12px;
    }

    .delete-btn {
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .delete-btn:hover {
        background-color: transparent;
        color: #222;
    }

</style>