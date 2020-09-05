<template>
  <div>
    <div class="main-calender">
      <div class="month-year">
        <select
          v-model="selectedMonth"
          class="month-select"
          @click="getCalender()"
        >
          <option v-for="(item, index1) in month" :key="index1">{{
            item.mon
          }}</option>
        </select>
        <select
          v-model="selectedYear"
          class="year-select"
          @click="getCalender()"
        >
          <option v-for="(year, index2) in years" :key="index2">{{
            year.year
          }}</option>
        </select>
      </div>
      <div class="grid-container grid-weekends">
        <div
          class="grid-day-item"
          v-for="(week, index3) in weeks"
          :key="index3"
        >
          {{ week.mon }}
        </div>
      </div>

      <div class="grid-container">
        <div
          class="grid-item"
          v-for="(previous, index4) in globalArr"
          :key="index4"
        ></div>
        <div class="grid-item" v-for="(day, index5) in daysArr" :key="index5">
          {{ day.day }}
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      // weeks: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
      weeks: [
        {
          id: 0,
          mon: "Sun",
        },
        {
          id: 1,
          mon: "Mon",
        },
        {
          id: 2,
          mon: "Tue",
        },
        {
          id: 3,
          mon: "Wed",
        },
        {
          id: 4,
          mon: "Thu",
        },
        {
          id: 5,
          mon: "Fri",
        },
        {
          id: 6,
          mon: "Sat",
        },
      ],
      daysArr: [],
      month: [
        {
          id: 0,
          mon: "January",
        },
        {
          id: 1,
          mon: "Feburary",
        },
        {
          id: 2,
          mon: "March",
        },
        {
          id: 3,
          mon: "April",
        },
        {
          id: 4,
          mon: "May",
        },
        {
          id: 5,
          mon: "June",
        },
        {
          id: 6,
          mon: "July",
        },
        {
          id: 7,
          mon: "August",
        },
        {
          id: 8,
          mon: "September",
        },

        {
          id: 9,
          mon: "October",
        },
        {
          id: 10,
          mon: "November",
        },
        {
          id: 11,
          mon: "December",
        },
      ],
      // years: [2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020],
      // years: [2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020],
      years: [
        {
          id: 0,
          year: 2012,
        },
        {
          id: 1,
          year: 2013,
        },
        {
          id: 2,
          year: 2014,
        },
        {
          id: 3,
          year: 2015,
        },
        {
          id: 4,
          year: 2016,
        },
        {
          id: 5,
          year: 2017,
        },
        {
          id: 6,
          year: 2018,
        },
        {
          id: 7,
          year: 2019,
        },
        {
          id: 8,
          year: 2020,
        },
      ],
      selectedMonth: "",
      selectedYear: 2012,
      getDate: new Date(),
      currentDayPosition: [],
      globalCurrentDate: "",
      globalObj: {},
      globalArr: [],
    };
  },

  mounted() {
    this.globalCurrentDate = this.getDate.getDate();
    var currentMonth = this.getDate.getMonth();
    var currentYear = this.getDate.getFullYear();
    this.selectedMonth = this.month[currentMonth].mon;
    this.selectedYear = currentYear;
    var endDate = new Date(currentYear, currentMonth + 1, 0).getDate();
    this.days = endDate;
    for (var j = 0; j < this.days; j++) {
      let newObj = {
        id: j,
        day: j + 1,
      };
      this.daysArr.push(newObj);
    }
    this.getDate.setDate(1);
    this.currentDayPosition = this.getDate.getDay();
    this.globalArr = [];
    for (var i = 0; i < this.currentDayPosition; i++) {
      var obj = {
        id: i,
        value: "",
      };
      this.globalArr.push(obj);
    }
  },

  methods: {
    getCalender() {
      console.log("reached here");
      console.log(this.years);
      var currentMonth = this.month.findIndex(
        (x) => x.mon === this.selectedMonth
      );
      var currentYear = this.selectedYear;
      this.selectedMonth = this.month[currentMonth].mon;
      this.selectedYear = currentYear;
      var endDate = new Date(currentYear, currentMonth + 1, 0).getDate();
      this.days = endDate;
      this.daysArr = [];
      for (var j = 0; j < this.days; j++) {
        let newObj = {
          id: j,
          day: j + 1,
        };
        this.daysArr.push(newObj);
      }
      this.getDate;
      var d = new Date(
        this.selectedYear,
        currentMonth,
        this.globalCurrentDate,
        0,
        0,
        0
      );
      d.setDate(1);
      this.currentDayPosition = [];
      this.currentDayPosition = d.getDay();
      this.globalArr = [];
      for (var i = 0; i < this.currentDayPosition; i++) {
        var obj = {
          id: i,
          value: "",
        };
        this.globalArr.push(obj);
      }
      console.log("1212", this.currentDayPosition);
    },
  },
};
</script>
<style lang="css">
.month-year {
  text-align: center;
}
.month-select {
  margin-right: 10px;
  padding: 5px;
  background: #fff;
  font-weight: bold;
}
.year-select {
  padding: 5px;
  background: #fff;
  font-weight: bold;
}
.grid-weekends {
  margin-top: 20px;
}
.grid-container {
  display: grid;
  grid-template-columns: 14.3% 14.3% 14.3% 14.3% 14.3% 14.3% 14.3%;
}
.grid-day-item {
  background-color: #83c9f4;
  border: 1px solid #e2dcd6;
  font-size: 16px;
  padding: 5px;
  text-align: center;
  font-weight: 600;
  color: #fff;
}
.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid #e2dcd6;
  padding: 25px 35px;
  font-size: 30px;
  text-align: center;
}
.grid-item:hover {
  background: grey;
  cursor: pointer;
}
@media (min-width: 320px) and (max-width: 480px) {
  .grid-item {
    padding: 10px;
  }
}
</style>
