<template>
     <div class="quadro">
          <h1>Indice de Massa Corpórea (IMC)</h1>
          <p>massa (Kg): </p>
          <input type="number" v-model="massa">
          <p>altura (m): </p>
          <input type="number" v-model="altura">
          <button  @click="visivel">calcular</button>
          <div v-if="mostrar">
               <div class="resp">{{imc()}}</div>  <!-- v-once   -->
               <div class="conclusao">{{conclusao()}}</div>
               <button @click="refazer">refazer</button>
          </div>
          

     </div>
</template>

<script>


export default {
     data() {
         return {
             massa: null,
             altura: null,
             mostrar: false,
             clica: 0,
             copia: null
         }
     },
     methods: {
         imc(resp, m, a) {
           m = this.massa
           a = this.altura
           resp = ((m)/(a**2)).toFixed(2)
           return resp 
         },
         visivel() {
             this.mostrar = true
         },
         conclusao() {
             if (this.imc() > 25) {
                 return `Você precisa perder ${(this.massa - 25*(this.altura)**2).toFixed(2)} kilos`
             }
             else {
                 //return this.imc()
                 return `Você está em forma`
             }
             
         },
         refazer() {
             this.mostrar = false
             this.altura = null
             this.massa = null
             if (this.imc != this.imc) {
                 this.imc == null
             }
             
         }
     },
     computed: {
        //
     }
}




</script>
    
<style>
    .quadro {
        width: 600px;
        height: 500px;
        background-color: rgb(255, 206, 116);
        margin: 15px;
        padding: 20px;
        border: solid 2px darkgreen;
        border-radius: 25px;
        display: flex;
        flex-direction: column;
        justify-content:inherit;
    }

    input {
        width: 150px;
        border-radius: 7px;
        border: solid 2px olive;

        padding-left: 8px;
        align-content: center;
    }

    p {
        color: white;
        font-weight:bolder;
        font-size: larger;
        font-family: Georgia, 'Times New Roman', Times, serif;
    }

    button {
        margin: 10px;
        width: 100px;
        height: 30px;
        background-color: rgba(37, 34, 197, 0.801);
        color: white;
        border: 1px solid rgb(177, 160, 160);
        border-radius: 15px;
        outline: none;
        
    }
     
    button:hover {
        background-color: rgba(106, 104, 236, 1); 
        color: white;
        border: 1px solid rgb(140, 119, 236);
    }

   
    .resp, .conclusao {
        background-color: white;
        width: 150px;
        height: 33px;
        align-content: center;
        border-radius: 12px;
        margin-top: 4px;

        align-content: center;
        justify-content: center;
        align-items: center;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

        border: solid 2px rgb(27, 133, 27);
    }

    .conclusao {
        width: 300px;
    }    
</style>