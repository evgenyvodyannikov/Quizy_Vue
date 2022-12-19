<template>
    <div>
        <div class="result">
            <img src="https://cdn-icons-png.flaticon.com/512/2278/2278992.png" />
            <h2>Ваш результат {{score}} из {{length}}</h2>
            <a href="/">
                <button class="button">Попробовать снова</button>
            </a>
        </div>
    </div>
</template>
  
<script>
export default {
    props: ['score', 'length'],
}

</script>
  
<style scoped>
@import "./style.scss";
</style>