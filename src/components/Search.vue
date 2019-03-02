<template>
    <div>
        <input type='text' placeholder='SEARCH' v-model='searchQuery'>
        <button v-on:click='changeNews'>SUBMIT</button>

    </div>
</template>

<script>
    export default {
        data: function(){
            return {
                searchQuery: " "
            }
        },
    methods: {
        changeNews(){
            this.$emit('newsChanged', this.searchQuery);
            this.searchQuery='';
            }
        }
    }
</script>


<style>



</style>