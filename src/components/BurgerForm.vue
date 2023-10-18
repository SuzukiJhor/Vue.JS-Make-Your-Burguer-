<template>
    <p>Componente de mensagem</p>
    <div>
        <form id="burger-form" @submit="createBurguer">
            <div class="input-container">
                <label for="name">Name Client</label>
                <input type="text" id="name" name="name" v-model="name" placeholder="Digite Seu nome">
            </div>
            <div class="input-container">
                <label for="bread">Choose your bread</label>
                <select name="bread" id="bread" v-model="bread">
                    <option value="">Choose </option>
                    <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">{{ bread.tipo }}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="meat">Choose your Meat</label>
                <select name="meat" id="meat" v-model="meat">
                    <option value="">Choose </option>
                    <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">{{ meat.tipo }}</option>
                </select>
            </div>
            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="optionais">Select options:</label>
                <div class="checkbox-container" v-for="optional in optionaisdata" :key="optional.id" :value="optional.tipo">
                    <input type="checkbox" name="optionais" v-model="optionais" :value="optional.tipo">
                    <spam>{{ optional.tipo }}</spam>
                </div>


            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Make  my burguer!">
            </div>
        </form>
    </div>
</template>


<script>
export default {
    name: "BurgerForm",
    data() {
        return {
            breads: null,
            meats: null,
            optionaisdata: null,
            name: null,
            bread: null,
            meat: null,
            optionais: [],
            status: 'Solicitado',
            msg: null
        }
    },
    methods: {
        async getIngredientes() {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();

            this.breads = data.paes;
            this.meats = data.carnes;
            this.optionaisdata = data.opcionais;
        },
        async createBurguer(e) {
            e.preventDefault();

            const data = {
                name: this.name,
                bread: this.bread,
                meat: this.meat,
                optionais: Array.from(this.optionais),
                status: "Solicitado"

            }
            console.log(data);
        }
    },
    mounted() {
        this.getIngredientes()
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
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
}

input,
select {
    padding: 5px 10px;
    width: 300px;
}

#optionais-container {
    flex-direction: row;
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
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}

.submit-btn:hover {
    background-color: transparent;
    color: #222;
}
</style>
