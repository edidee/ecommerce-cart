<template>
    <div class="wrapper">
        <div class="item-div">
        <div class="head">
           <h2>Shopping Cart <span>0</span></h2>
        </div>
        <div v-for="product in products" :key="product.id">
            <div class="flex-div">
               <div>
                   <input type="checkbox">
               </div>
            </div>
        </div>
        </div>
        <div class="summary-div">
            <p>ORDER SUMMARY</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Cart',
    data() {
        return {
            products: {},
            url: 'http://localhost:3000/products?_limit=10'
        }
    },
    methods: {
       async fetchAPIData() {
            try {
                const response = await this.$http.get(this.url)
                this.products = response.data
                console.log(response.data)
            } catch (error) {
                console.log(error);
            }
        }
    },
    mounted() {
        this.fetchAPIData()
    },
}
</script>

<style scoped>
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
    margin: 0 important;
}
.wrapper{
    display: flex;
    justify-content: space-between;
    width: 100%;
    /* margin: 2%; */
    background-color: #F2F2F2;
    height: 100vh;
}

.item-div{
    width: 55%;
    background-color: #FFFFFF;
    margin: 2%;
}

.item-div h2{
    text-align: center;
    margin-top: 1.5%;
}

.item-div span{
    background: orangered;
    color: #FFFFFF;
    padding: 1%;
    border-radius: 20%
}

.summary-div{
    width: 35%;
    background-color: #FFFFFF;
    margin: 2%;
}

.flex-div {
    display: flex;
}
</style>