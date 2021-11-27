<script>
    export default {
        props: {
            matched:{
                type: Boolean,
                default: false,
            },
            value: {
                type: Number,
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
        <div v-if="visible" class="card-face is-front">{{ value }} - {{ matched }}</div>
        <div v-else class="card-back is-back">Back</div>
        
    </div>
    
</template>

<style scoped>

.card {
    border: 5px solid #ccc;
    position: relative;
}
.card-face {
    width: 100%;
    height: 100%;
    position: absolute;
}
.card-back {
    width: 100%;
    height: 100%;
    position: absolute;
}

.card-face.is-front {
  background-color: red;
  color: white;
}

.card-back.is-back {
  background-color: blue;
  color: white;
}

</style>