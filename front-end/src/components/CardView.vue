<template>
    <section>
        <span></span>
        <div class="card-view" :key="book">
            <div class="book-title"> <h2> Book Title: {{book.title}}</h2></div>
            <div class="book-author"> <strong> Author: {{book.author}}</strong></div>
            <button class="button" @click="deleteBook">Delete</button>
        </div>
    </section>
</template>

<script>
export default {
    emits: [
        'delete-book'
    ],
    props: {
        book:Object
    },
    methods: {
        deleteBook() {
            this.$emit('delete-book', this.book.id);
        }
    }
}
</script>

<style scoped>
span {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    color: red;
}

section {
    margin-top: 2%;
    margin-left: 35%;
    border-radius: 7px;
    border-top: 5px solid red;
    width: 30%;
    background: #fff;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}

.card-view {
    box-sizing: border-box;
    width: 100%;
    padding: 10px;
    border-radius: 7px;
    border-bottom: 5px solid red;
}

.button {
    margin: 5px;
    background: #FF4742;
    border: 1px solid #FF4742;
    border-radius: 20px;
    box-shadow: rgba(0, 0, 0, 0.1) 1px 2px 4px;
    box-sizing: border-box;
    color: #FFFFFF;
    cursor: pointer;
    display: inline-block;
    font-family: nunito, roboto, proxima-nova, "proxima nova", sans-serif;
    font-size: 15px;
    font-weight: 800;
    line-height: 16px;
    min-height: 40px;
    outline: 0;
    padding: 12px 14px;
    text-align: center;
    text-rendering: geometricprecision;
    text-transform: none;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    vertical-align: middle;
}

.button:hover,
.button:active {
    background-color: initial;
    background-position: 0 0;
    color: #FF4742;
}

.button:active {
    opacity: .5;
}
.book-title{
    width: 100%;
}
.book-author{
    padding: 5px;
}
</style>