<template>
  <v-dialog
    v-if=" istimetoDisplay"
      v-model="istimetoDisplay"
      width="500"
      @click:outside="onClose"
      >


      <v-card>
 
  <v-card-title
          class="headline blue lighten-2"
          primary-title
        >
         {{fruit_data.name}}
        </v-card-title>

        <v-card-text>
            <v-img :src="fruit_data.img"/>
            qty : {{fruit_data.qty}}
        </v-card-text>

      </v-card>
  </v-dialog>
</template>
<script>
export default {
    
    props:["fruit_data"],
    data:()=>({ dialog:false,}),

    methods:{
        onClose()
        {
  
            this.$emit('dialogClose');
        },
        
       
    },
    computed:{
       
        istimetoDisplay:{
            get:function()
            {
                this.dialog = false;

                if(typeof this.fruit_data != 'undefined' && this.fruit_data != null)
                    this.dialog = true;
            
            

            return this.dialog;
            },

            set:function(newval)
            {
     
                //return newval;
            }
        }
    },
    created(){
        console.log("created:",this.fruit_data);
    },
    updated(){
        console.log("updated:",this.fruit_data);
    }
}
</script>