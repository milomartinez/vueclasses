<template>
  <div>
  <v-container id="app" >
   <v-row>
     <v-col>
      <v-row v-for="fruit of fruits" :key="fruit.name">
        <v-col cols = "2" align="left">
        {{fruit.name}}    : 
        </v-col>
        <v-col  cols = "6"  align="left">
          <v-row >
            <v-col cols="4">
            <v-text-field              
              outlined
              v-model.number="fruit.qty"/>
            </v-col>
            <v-col cols="4">
              <v-btn     @click="fruit.qty++">+</v-btn>
            </v-col>
            <v-col cols="4">
              <v-btn     @click="viewFruit(fruit)" >view</v-btn>
            </v-col>
            </v-row>
        </v-col>
        <v-col cols="4" align="left">
          <span v-if="fruit.qty === 0"> - Out of Stock </span>
        </v-col>
       
      </v-row>
     </v-col>
   </v-row> 
   <v-row>
     <h1> Total: {{sumFruits}}</h1>
   </v-row>
  <FruitCard :fruit_data="fruit2display" v-on:dialogClose="shutDialog"/>
  </v-container>
  </div>
</template>

<script>
import FruitCard from "@/components/fruitcard"
// @ is an alias to /src


export default {
  name: 'home',

  data:()=>({

 
    fruit2display:null,
    total:0,
    fruits:[
      {name:"apple",  qty:10, img:"./apple.jpg"},
      {name:"banana", qty:0,  img:"./banana.jpg"},
      {name:"peach",  qty:1,  img:"./peach.jpg"},
    ],
  }),
  components: {FruitCard, },

  methods:{

     sumFruitsMth(){

      this.total = 0 ;
      for (var fruit of this.fruits)
        this.total += fruit.qty
      
      return this.total
    },
    viewFruit(fruit)
    {
      this.fruit2display = fruit;
   

    },

    shutDialog()
    {
   
          this.fruit2display = null;

    }
   
  },
  computed:{

    sumFruits(){

      this.total = 0 ;
      for (var fruit of this.fruits)
        this.total += fruit.qty
      
      return this.total
    }
  }
}
</script>
