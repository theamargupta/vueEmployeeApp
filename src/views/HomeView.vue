<script setup>
import { ref } from 'vue'
import SideBar from '../components/SideBar.vue'
import CardComp from '../components/CardComp.vue'
import json from '../assets/employees.json'
const employeeData = ref(json)
const selectedUser = ref({})
const setEmployee = (selected) => {
  selectedUser.value = selected
}
const finalArrConv = ({ arr }) => {
  const finalRes = {}
  Array.from(new Set(arr?.map((data) => data.manager_id))).forEach((data2) => {
    arr.forEach((data3) => {
      if (data2 === data3.manager_id) {
        if (finalRes[data3.manager_id]?.emp) {
          finalRes[data3.manager_id].emp.push(data3)
        } else {
          finalRes[data3.manager_id] = { mng: {}, emp: [data3] }
        }
      }
    })
    arr.forEach((data3) => {
      if (data2 === data3.id) {
        finalRes[data2].mng = data3
      }
    })
  })
  return Object.values(finalRes).filter((data) => Object.keys(data.mng).length)
}

const output = ref(finalArrConv({ arr: employeeData.value }))
const deleteEmployee = (id) => {
  console.log('click')
  const output2 = employeeData.value.filter((data) => data.id !== id)
  employeeData.value = output2
  return (output.value = finalArrConv({ arr: output2 }))
}
</script>
<template>
  <SideBar :output="output" @setEmployee="setEmployee">
    <main>
      <CardComp
        :title="selectedUser.first_name + selectedUser.last_name"
        :subtitle="selectedUser.username"
        :address="selectedUser.street_address + selectedUser.city"
        :bio="selectedUser.bio"
        :avatar="selectedUser.profile_pic"
        :email="selectedUser.email"
        :gender="selectedUser.gender"
        :id="selectedUser.id"
        @deleteEmployee="deleteEmployee"
      />
    </main>
  </SideBar>
</template>
