<template>
    <form @submit.prevent="addBook">
        <span>Add Book</span>
        <div class="form-input">
            <input type="text" class="title" placeholder="Book Title" v-model="title">
            <input type="text" class="author" placeholder="author" v-model="author">
            <button class="button" >Add Book</button>
        </div>
    </form>
</template>

<script>
export default {
    emits: ['add-Book'],
    data() {
        return {
            title: "",
            author: "",
        }
    },
    methods: {
        addBook() {
            let newBook = { title: this.title, author: this.author }
            this.$emit("add-Book", newBook)
            console.log(newBook.title);
            this.title = "";
            this.author = "";
        }
    }
   
}
</script>

<style scoped>

    form{
    background: rgb(0, 204, 255);
    }
    span {
        display: flex;
        justify-content: center;
        align-items: center;    
        font-size: 2rem;
        color: #fff;
    }
form {
    border-radius: 7px;
    border-top: 5px solid red;
    width: 30%;
    margin: auto;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    position: fixed;
    top: 0;
    left:  0;
    right: 0;
    z-index:9999;
}

.form-input input {
    box-sizing: border-box;
    width: 95%;
    margin: 10px;
    margin-left: 2.5%;
    padding: 10px;
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
    color: #fff;
}

.button:active {
    opacity: .5;
}
</style>