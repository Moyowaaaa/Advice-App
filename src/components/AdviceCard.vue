<template>
    <div>
    

        <div class="main">
              <!-- <button @click="advice">Get Advice</button> -->

              <div class="card">
                <div class="card-header">
                  
                </div>
               
                <div class="card-body">
                  <div>
                       <p>#{{id}} </p>
                       <hr/>
                </div>
                  <p>"{{ advice }}"</p>
                </div>
                <div>
                     <button @click="getAdvice"><img src="..\assets\dice.svg" width="25"></button>
                </div>
              </div>
        </div>
      
    </div>
</template>

<script>
 import axios from 'axios'


export default {
    name:'AdviceCard',
    data() {
        return {
            advice:'',
            id:''
        }
    },
    mounted () {
        this.getAdvice()
    },
    methods:{
        async getAdvice () {
            try {
                const response = await axios.get('https://api.adviceslip.com/advice')
          
                this.advice = response.data.slip.advice
                this.id = response.data.slip.id
            } catch (error) {
                console.log(error)
            
                
            }
        }
    }

}
</script>




<style scoped>
.main {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
     background-color: rgb(49, 58, 72);
    
}
.card{
    width:40%;

    height: auto;
    border-radius: 20px;
    box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: blue;
    padding-top: 2%;
    padding-bottom: 2%;
}
button{
    height:5rem;
    width: 5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgb(49, 58, 72);
    outline: none;
    border:none;
    border-radius: 50%;
    box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
}

.card-body{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-left:2%;
    padding-right: 2%;

}
.card-body p{
    font-size:30px;
    color: white;
    text-align: center;
    font-family: 'Roboto', sans-serif;
    
}
button:hover{
    background: skyblue;
}

@media screen and (max-width: 485px){
    .card{
        width:90%;
    }
    .card-body p {
        font-size:20px;
    }
}
@media screen and (min-width: 486px) and (max-width: 900px){
    .card{
        width:90%;
    }
    .card-body p {
        font-size:20px;
    }


}
</style>