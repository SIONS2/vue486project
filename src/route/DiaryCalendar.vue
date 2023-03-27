<template>
  <div class="DiaryCalendar">
    <ul class="calendarWrap">
      <li></li>
      <li>
        <VCalendar 
          borderless
          transparent
          expanded
        />
      </li>
      <li></li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';
import { VCalendar } from 'v-calendar';
import 'v-calendar/style.css';

const dates = ref(new Date());

export default {
  components: {
    VCalendar
  },
  setup() {
    return { dates };
  }
};

</script>

<style scoped>
.DiaryCalendar {
  width: 100%;
  height: 100%;
  }
.calendarWrap {
  display: flex;
  width: 100%;
  height: 83%;
  margin-top: 2%;
}
.calendarWrap >li {
    width: 75%;
    height: 100%;
    margin: auto;
    border-radius: 15px;
    background-color: #C1B2B2;
    margin:0 2.5%;
}
.calendarWrap >li:nth-child(1){
  width: 10%;
  border-top-left-radius:0px;
  border-bottom-left-radius: 0px;
}
.calendarWrap >li:nth-child(3){
  width:10%;
  border-top-right-radius: 0px;
  border-bottom-right-radius:0px;
  
}
</style>
