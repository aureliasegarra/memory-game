<script>
    export default {
        props: {
            matched:{
                type: Boolean,
                default: false,
            },
            value: {
                type: String,
                required: true,
            },
            visible: {
                type: Boolean,
                default: false,
            },
            position: {
                type: Number,
                required: true,
            }
        },
        setup(props, context){
            const turnCard = () => {
                context.emit('turn-card',{
                    //position inside of the list
                    position: props.position,
                    frontValue: props.value,
                })
            }
            return {
                turnCard
            }
        }
       
    }
</script>

<template>
    
    <div class="card" @click="turnCard">
        <div v-if="visible" class="card-face is-front">
            <img :src="`/images/${value}.png`" :alt="value" class="image-face">
            <img v-if="matched" src="../../public/images/checked.png" class="icon-checkmark" alt="checked icon">
        </div>
        <div v-else class="card-back is-back"></div>
        
    </div>
    
</template>

<style scoped>

.card {
    position: relative;
   
}
.card-face {
    width: 100%;
    height: 100%;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    
    
}
.card-back {
    width: 100%;
    height: 100%;
    position: absolute;
}

.card-face.is-front {
  background-color: rgb(66, 65, 65);
  color: white;
  border-radius: 10px;
}

.card-back.is-back {
  background-image:url('../../public/images/vue.png');
  background-size: cover;
  background-position: center;
  color: white;
  border-radius: 10px;
}

.icon-checkmark {
    position: absolute;
    right: 5px;
    bottom: 5px;
    width: 20%;
}

.image-face {
    width: 70%;
}

</style>