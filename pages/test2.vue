<template>
  <div class="container">
    
         <div>
      <h1>TEST 2 LOOP</h1>
      </div>
      <table>
       <thead class="header">
          <tr>
            <th v-for="(header, index) in headers" :key="index" :class="{'time-header': header === 'TIME'}">
              {{ header }}
            </th>
          </tr>
        </thead>
       <tbody class="first-row">
          <tr v-for="(row, rowIndex) in datas" :key="rowIndex" :class="{
              'stripe-light': getClass(row.name) === 'stripe-light',
              'stripe-dark': getClass(row.name) === 'stripe-dark',
              
            }">
            <td >{{ row.name }}</td>
            <td :class="{'border-bottom': getBottomBorder(row.name, rowIndex),
              'border-top': getTopBorder(row.name, rowIndex)}">{{ row.day }}</td>
            <td :class="{'border-bottom': getBottomBorder(row.name, rowIndex),
              'border-top': getTopBorder(row.name, rowIndex)}"> 
              <div class="button-container">
                <button class="button-style">{{ row.startTime }}</button> - 
                <button class="button-style">{{ row.endTime }}</button>
              </div>
              </td>
            <td :class="{'border-bottom': getBottomBorder(row.name, rowIndex),
              'border-top': getTopBorder(row.name, rowIndex)}">{{ row.hall }}</td>
          </tr>
        </tbody>
      </table>
    
  </div>
</template>

<script setup>
import { ref } from 'vue'

const getClass = (teamName) => {
  const uniqueTeams = [...new Set(datas.map(data => data.name))]
  console.log('uniqueTeams: ', uniqueTeams);
  const teamIndex = uniqueTeams.indexOf(teamName)
  return teamIndex % 2 === 0 ? 'stripe-dark' : 'stripe-light'
}
const getBottomBorder = (teamName, rowIndex) => {
  if (rowIndex === datas.length - 1) return false; // No border for the last row
  const nextRow = datas[rowIndex + 1];
  return nextRow.name === teamName;
}

// Determine if a row should have a top border
const getTopBorder = (teamName, rowIndex) => {
  if (rowIndex === 0) return false; // No border for the first row
  const previousRow = datas[rowIndex - 1];
  return previousRow.name === teamName;
}

const headers = ref(['TEAM', 'DAY', 'TIME','HALL'])
const datas = ([
  {name:"U8 mix",day:'Friday',startTime:'15:30',endTime:'16:45',hall:'Deusterschule Kitzingen'},
  {name:"U10 mix",day:'Friday',startTime:'17:00',endTime:'18:30',hall:'Deusterschule Kitzingen'},
  {name:"U10 mix",day:'Friday',startTime:'16:45',endTime:'18:15',hall:'Deusterschule Kitzingen'},
  {name:"U12 mix",day:'Thursday',startTime:'17:35',endTime:'18:45',hall:'Mainstockheim'},
  {name:"U12 mix",day:'Thursday',startTime:'11:00',endTime:'12:30',hall:'Mainstockheim'},
  {name:"U14 m",day:'Thursday',startTime:'16:30',endTime:'18:30',hall:'Arena Kitzingen'},
  {name:"U14 m",day:'Thursday',startTime:'17:00',endTime:'18:30',hall:'Arena Kitzingen'},
  {name:"U14 w",day:'Thursday',startTime:'17:00',endTime:'18:30',hall:'Arena Kitzingen'},
  {name:"U14 w",day:'Thursday',startTime:'18:30',endTime:'20:30',hall:'Arena Kitzingen'},
  {name:"U16 m",day:'Thursday',startTime:'16:30',endTime:'18:30',hall:'Arena Kitzingen'},
  {name:"U16 m",day:'Thursday',startTime:'18:30',endTime:'20:00',hall:'Arena Kitzingen'},
  {name:"U18/20 Damon",day:'Thursday',startTime:'18:30',endTime:'20:00',hall:'Arena Kitzingen'},
  {name:"U18/20 Damon",day:'Thursday',startTime:'18:30',endTime:'20:30',hall:'Arena Kitzingen'},
  {name:"U18 m",day:'Thursday',startTime:'20:30',endTime:'22:00',hall:'Arena Kitzingen'},
  {name:"U18 m",day:'Thursday',startTime:'18:30',endTime:'20:00',hall:'Arena Kitzingen'},
  {name:"U20 / Men",day:'Sunday',startTime:'20:30',endTime:'22:00',hall:'Arena Kitzingen'},
  {name:"U20 / Men",day:'Sunday',startTime:'20:00',endTime:'21:30',hall:'Arena Kitzingen'},
  {name:"OPEN COURT",day:'Sunday',startTime:'15:00',endTime:'16:00',hall:'Arena Kitzingen'}
])

</script>

<style  scoped>
*{
  font-family: Helvetica, Arial, sans-serif;
}
/* @media (min-width: 1200px) { */
.container {
  margin: 0 auto;
  width: 1440px; /* Fixed width for desktop */
}
/* } */

.first-row{
  border-top: 1px solid black
}
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: none;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #ffffff;
}
th.time-header {
  text-align: center;
}
.border-bottom {
  border-bottom: 1px solid rgb(175, 172, 172);
}

.border-top {
  border-top: 1px solid rgb(210, 210, 210);
}

.stripe-light {
  background-color: #f9f9f9;
}

.stripe-dark {
  background-color: #eeeded;
}

.button-style {
  background-color: #838486;
  color: white; 
  padding: 10px 20px;
  border: none; 
  border-radius: 30px;
  text-align: center;
  font-size: 1rem; /* Adjust font size */
  font-weight: bold; /* Make text bold */
  margin-left: 10px;
  margin-right: 10px;
}
.button-container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
}

</style>