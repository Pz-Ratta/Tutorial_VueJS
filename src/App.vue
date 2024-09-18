<template>
  <section>
    <form></form>
    <img :src=picture :width="size" :height="size" ref="imageEL" /><br>

    <h1>ชื่อ: {{ getFullName }}</h1>
    <h1>อายุ: {{ age }} ปี</h1>
    <h1>เงินเดือน: {{ salary }} บาท</h1>
    <h1>รายได้ต่อปี: {{ getIncome }} บาท</h1>
    <h1>ตำแหน่ง: {{ getDepartment }}</h1>
    <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>

    <button @click="toggleVisible">{{ isVisible ? "ซ่อน" : "แสดง" }}รายละเอียด</button>
    <article v-show="isVisible">
      <a>ที่อยู่: <span v-html="address"></span></a>
      <p>Social: <a :href="social" target="_blank">facebook</a></p>
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก: </p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index"> {{ index + 1 }}. {{ item }} </li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน</p>
      <ul>
        <li v-for="(item, key) in general" :key="key"> {{ key }}. {{ item }} </li>
      </ul>
    </article>
  </section>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstname: "PPP",
      lastname: "zzz",
      age: 20,
      address: "<strong>กรุงเทพฯ</strong>",
      picture: "https://uxwing.com/wp-content/themes/uxwing/download/peoples-avatars/corporate-user-icon.png",
      size: 150,
      social: "https://ppppp.com",
      hobby: ["ssss", "11111", "2222", "33333", "2345"],
      general: {
        gender: "ชาย",
        weight: 80,
        height: 170,
        status: false
      },
      isVisible: false,
      salary: 25000
    }
  },
  methods: {
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
    addSalary(value) {
      this.salary += value;
    }
  },
  computed:{
    getFullName() {
      return this.firstname + " " + this.lastname
    },
    getIncome(){
      return this.salary * 12;
    },
    getDepartment() {
      return this.salary>=35000? "Project Manager": "Programmer";
    }
  },
  watch:{
    salary(value) {
      if(value > 50000){
        alert("เงินเดือนไม่ควรเกิน 50000 บาท");
        setTimeout(()=>{
          this.salary = 20000;
        }, 2000)
      }
    }
  }

}
</script>

<style></style>
