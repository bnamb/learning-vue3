<template>
<div class="m-auto mt-16 text-gray-700">
    <h1 class="text-5xl my-4 text-center">Vue Calendar</h1>
    <section class="font-bold flex justify-between">
        <h2>{{currentMonthName}}</h2>
        <h2>{{currentYear}}</h2>
    </section>
    <section class="flex my-2">
        <p class="p-2 text-center" style="width: 14.24%" v-for="day in days" :key="day">{{day}}</p>
    </section>
    <section class="flex flex-wrap">
        <p class="text-center" style="width: 14.24%" v-for="num in startDay()" :key="num"></p>
        <p class="text-center" style="width: 14.24%" v-for="num in daysInMonth()" :key="num" :class="currentDateClass(num)">{{num}}</p>
    </section>
    <section class="flex justify-between my-4">
        <button class="px-4 py-1 border rounded rounded-2xl bg-gradient-to-tr from-yellow-200 via-pink-200 to-pink-400" @click="prev">Prev</button>
        <button class="px-4 py-1 border rounded rounded-2xl bg-gradient-to-tr from-yellow-200 via-pink-200 to-pink-400" @click="next">Next</button>
    </section>
</div>
</template>

<script>
export default {
    data() {
        return {
            currentDate: new Date().getUTCDate(),
            currentYear: new Date().getFullYear(),
            currentMonth: new Date().getMonth(),
            days:["Sun","Mon","Tue","Wed","Thu","Fri","Sat"]
        }
    },
    methods:{
        daysInMonth() {
            return new Date(this.currentYear, this.currentMonth +1, 0).getDate();
        },
        startDay(){
            return new Date(this.currentYear, this.currentMonth, 1).getDay();
        },
        next(){
            if(this.currentMonth === 11) {
                this.currentMonth = 0;
                this.currentYear++
            } else {
                this.currentMonth++
            }
        },
        prev(){
            if(this.currentMonth === 0){
                this.currentMonth = 11;
                this.currentYear--
            } else {
                this.currentMonth--
            }
        },
        currentDateClass(num){
            const calendarFullDate = new Date(this.currentYear,this.currentMonth,num).toDateString();
            const currentFullDate = new Date().toDateString();
            return calendarFullDate === currentFullDate ? "text-yellow-600" : "";
        }
    },
    computed:{
        currentMonthName(){
            return new Date(this.currentYear, this.currentMonth).toLocaleString("default",{month: 'long'})
        }
    }
}
</script>

<style>

</style>