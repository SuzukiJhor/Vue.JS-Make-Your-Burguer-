<template>
    <p>Componente de mensagem</p>
    <div>
        <form id="burger-form">
            <div class="input-container">
                <label for="name">Name Client</label>
                <input type="text" id="name" name="name" v-model="name" placeholder="Digite Seu nome">
            </div>
            <div class="input-container">
                <label for="bread">Choose your bread</label>
                <select name="bread" id="bread" v-model="bread">
                    <option value="">Choose </option>
                    <option value="integral">integral</option>
                </select>
            </div>
            <div class="input-container">
                <label for="meat">Choose your Meat</label>
                <select name="meat" id="meat" v-model="meat">
                    <option value="">Choose </option>
                    <option value="rump-steak">rump steak</option>
                </select>
            </div>
            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="optionais">Select options:</label>
                <div class="checkbox-container">
                    <input type="checkbox" name="optionais" v-model="optionais" value="salame">
                    <spam>Salame</spam>
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
    name: "BurgerForm"
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
