<template>
    <p>Componente de mensagem</p>
    <div>
        <form id="burger-form">
            <div class="input-container">
                <label for="name">Name Client</label>
                <input type="text" id="name" name="name" v-model="name" placeholder="Digite Seu nome">
            </div>
        </form>
    </div>
</template>


<script>
export default {
    name: "BurgerForm"
}
</script>

<Style scoped>

    </Style>
