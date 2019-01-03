<template>
    <div class="result" :class="{wrong: !result}">
        <span v-if="result">Resposta Certa! =)</span>
        <span v-else>Resposta Errada! =)</span>
        <hr>
        <button @click="$emit('confirmed')">Próxima pergunta</button>
    </div>
</template>

<script>
export default {
    props:{
        result:{
            type: Boolean,
            required: true
        }
    }
}
</script>

<style>
    .result{
        height: 500px;
        color: #fff;
        background-color: #fff;
        border-radius: 20px;
        font-size: 5.5rem;

        display: flex;
        flex-direction: column;
        justify-content: center;
        background-color: #89c454;
    }

    .result hr {
        color: #fff;

    }

    .result.wrong{
        background-color: #f05250;
    }

    .result button{
        outline: none;
        align-self: center;
        padding: 10px 20px;
        font-size: 1.7rem;
        border-radius: 8px;
        background-color: #fff;
        color:#30863d;
        font-weight: 600;
    }

    .result.wrong button{
        color: red;
    }
</style>





