<template>
    <div class="backdrop">
        <div class="modal" :class="{sale: theme === 'sale'}">
            <h1>Modal Box</h1>
            <slot></slot>
            <button @click="closeModal">Close</button>
        </div>
    </div>
</template>

<script>

export default {
    props: [ 'theme'],
    methods: {
        closeModal(){
            this.$emit('close') //custom event listens to  parent component. name of event is custom
        }
    }
}

</script>


<style scoped>
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
    }

.modal.sale {
        background: crimson;
        color: white;
    }
.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}
h1 {
    color: blue;
}
</style>