
<template>
  <input type="text" v-model="detail" /> <button v-if="detail" @click="addRecord">Add</button>
  <ul>
    <li v-for="(record,index) in filteredRecords" :key="index" :style="{color: 'black', backgroundColor: record.color }"> color: {{ record.color }}, type: {{ record.type }}, registration: {{ convertDate(record.registration) }}, capacity: {{ record.capacity }} <button @click="removeRecord(index)" v-if="!detail">Remove</button></li>
  </ul>
</template>

<script>
export default {
  data: () => ({
    records: [
    {
        "color": "purple",
        "type": "minivan",
        "registration": "2017-01-03T00:00:00.000Z",
        "capacity": 7
    },
    {
        "color": "red",
        "type": "station wagon",
        "registration": "2018-03-03T00:00:00.000Z",
        "capacity": 5
    },
    {
        "color": "blue",
        "type": "minivan",
        "registration": "2017-01-03T00:00:00.000Z",
        "capacity": 7
    },
    {
        "color": "green",
        "type": "station wagon",
        "registration": "2018-03-03T00:00:00.000Z",
        "capacity": 5
    },
    {
        "color": "grey",
        "type": "minivan",
        "registration": "2017-01-03T00:00:00.000Z",
        "capacity": 7
    },
    {
        "color": "blue",
        "type": "station wagon",
        "registration": "2018-03-03T00:00:00.000Z",
        "capacity": 5
    },
    {
        "color": "orange",
        "type": "minivan",
        "registration": "2017-01-03T00:00:00.000Z",
        "capacity": 7
    },
    {
        "color": "yellow",
        "type": "station wagon",
        "registration": "2018-03-03T00:00:00.000Z",
        "capacity": 5
    },
    null,
    {
        "color": "white",
        "type": "station wagon",
        "registration": "2018-03-03T00:00:00.000Z",
        "capacity": 5
    },
],

  detail: ''
  }),

  computed: {
    filteredRecords() {
      return this.records.filter(record => {
      if(record && !this.detail) {
        return true;
      }
        
      for(let prop in record) {
        if(record[prop] == this.detail) {
          return true;
        }
      }
      return false;
      })
    }
  },

  methods: {
    convertDate(date) {
      let dateStr = new Date(date).toISOString();
      return dateStr.split("T")[0];
    },
    addRecord() {
      let index = this.filteredRecords.length - 1;
      this.records = [...this.records, this.filteredRecords[index]];
    },
    removeRecord(i) {
      this.records = this.records.filter((record,index) => index != i);
    }
  }
}
</script>
