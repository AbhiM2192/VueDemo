<template>
    <div>
         <h2>Full Name : {{fullName}}</h2>
         <button @click="changeFullName">Change Fullname</button>
    <button @click="addItem">Add Items</button>
    <div v-if="add">
        <input type="text" id="title" v-model="title"/>
        <input type="number" id="price" v-model.number="price">
        <button @click="AddItems">Submit</button>
    </div>
    <h2>Total Price : {{total}}</h2>
    <!-- <template v-for="item in goods" :key="item.id">
        <h2 v-if="item.price > 100">{{item.title}} ... {{item.price}}</h2> 
    </template> -->
    <h2 v-for="item in expensiveItems" :key="item.id"> {{item.title}} ... {{item.price}}</h2>
    </div>
   
</template>

<script>
export default {
    name:'ComputedPropDemo',
    data(){
        return{
            firstName:'Abhishek',
            lastName:'Biyani',
            title:'',
            price:null,
            goods:[
                {
                    id:1,
                    title:'TV',
                    price:100
                },
                {
                    id:2,
                    title:'Phone',
                    price:200
                },
                {
                    id:3,
                    title:'Laptop',
                    price:300
                }
            ],
            add:false
        }
    },
    methods:{
        addItem(){
            this.add = true
        },
        AddItems(){
            this.goods.push({id:this.goods.length+1,title:this.title,price:this.price});
            this.title = '';
            this.price = null;
        },
        changeFullName(){
            this.fullName = 'Tony Stark'
        }
    },
    computed:{
        fullName :{
            get(){
                return `${this.firstName} ${this.lastName}`
            },
            set(value){
                const names = value.split(' ');
                this.firstName = names[0]
                this.lastName = names[1]
            }
        },
        total(){
            return this.goods.reduce((total,curr) => (total = total +curr.price),0)
        },
        expensiveItems(){
            return this.goods.filter(item => item.price > 100)
        }
    }
}
</script>