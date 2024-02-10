<template>
  <div id="app">
    <sc
      :schedule-data="scData"
      :setting="setting"
      @row-click-event="rowClickEvent"
      @date-click-event="dateClickEvent"
      @click-event="clickEvent"
      @add-event="addEvent"
      @move-event="moveEvent"
      @edit-event="editEvent"
      @delete-event="deleteEvent"
    ></sc>
  </div>
</template>

<script>
import schedulerLite from "./components/schedulerLite.vue";
import { ref } from 'vue';


const sampleData = [
  {
    title: "Кол-во номеров",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "2",
        start: "2024/02/21 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "2",
        start: "2024/02/14 00:00",
        end: "2024/02/14 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Цена /номер",
    noBusinessDate: [],
    businessHours: [
      {
        start: "0:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "2500",
        start: "2024/02/20 00:00",
        end: "2024/02/20 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Цена /место (2-х)",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "2500",
        start: "2024/02/18 00:00",
        end: "2024/02/18 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Цена / место (3-х)",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "1500",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "1600",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Цена / место (4-х)",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "1500",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "1600",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Cashback",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "150",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "160",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Cashback (%)",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "15%",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "16%",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Cashback без заезда",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "100",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "100",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
  {
    title: "Cashback без заезда (%)",
    noBusinessDate: [],
    businessHours: [
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
      {
        start: "00:00",
        end: "24:00",
      },
    ],
    schedule: [
      {
        text: "5",
        start: "2024/02/21 00:00",
        end: "2024/02/21 24:00",
        data: {
          something: "something",
        },
      },
      {
        text: "5",
        start: "2024/02/22 00:00",
        end: "2024/02/22 24:00",
        data: {
          something: "something",
        },
      },
    ],
  },
];

const sampleSetting = {
  startDate: "2024/1/14",
  endDate: "2024/12/31",
  weekdayText: ["ВС", "ПН", "ВТ", "СР", "ЧТ", "ПТ", "СБ"],
  unit: 1440, // Minutes
  borderW: 1, // Px
  dateDivH: 25, // Px
  timeDivH: 25, // Px
  unitDivW: 50, // Px
  titleDivW: 10, // Percent
  rowH: 75, // Px
};

const month = ref({
  month: new Date().getMonth(),
  year: new Date().getFullYear(),
});

const format = (date) => {
  const month = date.getMonth();
  const year = date.getFullYear();
  let monthArray = ["Январь", "Февраль", "Март", "Апрель", "Май", "Июнь", "Июль", "Август", "Сентябрь", "Октябрь", "Ноябрь", "Декабрь"];
  let monthText = monthArray[month];
  return `${monthText}, ${year}`;
};



export default {
  name: "App",
  components: {
    sc: schedulerLite,
  },
  data: function () {
    return {
      scData: sampleData,
      setting: sampleSetting,
      month,
      format
    };
  },
  methods: {

    dateClickEvent(date) {
      console.log("------");
      console.log("DateClickEvent:");
      console.log("Date:" + date);
    },
    rowClickEvent(rowIndex, text) {
      console.log("------");
      console.log("RowClickEvent:");
      console.log("RowIndex:" + rowIndex);
      console.log("RowTitle:" + text);
    },
    
    clickEvent(startDate, endDate, text, other) {
      console.log("------");
      console.log("ClickEvent:");
      console.log("StartDate:" + startDate);
      console.log("EndDate:" + endDate);
      console.log("ContentText:" + text);
      
      if (other) {
        console.log("OtherData:");
        console.log(other);
      }
    },
    addEvent(rowIndex, startDate, endDate) {
      console.log("------");
      console.log("AddEvent:");
      console.log("RowIndex:" + rowIndex);
      console.log("StartDate:" + startDate);
      console.log("EndDate:" + endDate);
    },
    moveEvent(status, newStartDate, newEndDate) {
      console.log("------");
      console.log("MoveEvent:");
      if (status == 1) {
        console.log("NewStartDate:" + newStartDate);
        console.log("NewEndDate:" + newEndDate);
      } else if (status == 2) {
        console.log("Has other event, can't move.");
      } else {
        console.log("Not businessDay, can't move.");
      }
    },
    editEvent(newStartDate, newEndDate) {
      console.log("------");
      console.log("EditEvent:");
      console.log("NewStartDate:" + newStartDate);
      console.log("NewEndDate:" + newEndDate);
    },
    deleteEvent(row, index) {
      console.log("------");
      console.log("DeleteEvent:");
      console.log("Row:" + row);
      console.log("Index:" + index);
    },
    addNewRow() {
      let newTitle = "Room" + (this.scData.length + 1);
      this.scData.push({
        title: newTitle,
        noBusinessDate: [],
        businessHours: [
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
          {
            start: "00:00",
            end: "24:00",
          },
        ],
        schedule: [],
      });
    },
  },
};
</script>

<style>
.sample {
  width: 10px;
  height: 10px;
  margin: 5px;
  border: 1px solid black;
}

.cant-res {
  background-color: #999 !important;
}

.reserved {
  background-color: #ec920a !important;
}
</style>