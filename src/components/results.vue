<template>
<h3>your total number of clicks were:</h3>
<h2> {{score}} </h2>
</template>

<script>
export default {
    props: ['score']

}
</script>

<style>
h2{
    font-size: 40px;
}

</style>