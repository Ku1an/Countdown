<script setup>
import { onMounted, reactive } from 'vue';



    function setCountDown() {
        const currentDate = new Date()
        const endDate = new Date("2025-03-07")
        const timeLeft = Math.abs(currentDate - endDate + (1000 * 60 * 60))
        const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
        const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

        countDown.days = days
        countDown.hours = hours
        countDown.minutes = minutes,
        countDown.seconds = seconds
    }

    const countDown = reactive({
        days: 0,
        hours: 0,
        minutes: 0,
        seconds: 0,
    })
    setCountDown()

    onMounted(() => {
        setInterval(() => {
            setCountDown();
        },1000)
    })

</script>

<template lang="">
    <div class="container2">
        <div class="countdown-container"> 
            {{ countDown.days }}d
            {{ countDown.hours }}h
            {{ countDown.minutes }}m 
            <span class="simme"> {{ countDown.seconds }} </span> s
        </div>
    <div class="textBox"><p> SNART <span class="simmeGreen">HEMMA</span> LILLEN! KÄMPA <3 </p> </div>

    </div>
</template>

<style scoped>

.container2 {
    height: 100%;

    font-size: 2.5rem;
}

.countdown-container {
    display: flex;
    height: 60%;
    justify-content: center;
    align-items: center;
}


.simme {
    color: yellow;
    margin-left: 17px;
}
.simmeGreen {
    color: green;
}


.textBox {
    display: flex;
    justify-content: center;
}

</style>