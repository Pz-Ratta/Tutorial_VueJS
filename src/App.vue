<template>
  <section>
    <img :src=picture :width="size" :height="size"/><br>
    ป้อนชื่อเล่น: <input type="text"/>
    <h1>ชื่อ: {{ getFullName() }}</h1>
    <h1>อายุ: {{ age }} ปี</h1>
    <a>ที่อยู่: <span v-html="address"></span></a>
    <p>Social: <a :href="social" target="_blank">facebook</a></p>
    <p>งานอดิเรก: </p>
    <ul>
      <li>{{ hobby[0] }}</li>
      <li>{{ hobby[1] }}</li>
      <li>{{ hobby[2] }}</li>
    </ul>
    <p>ข้อมูลพื้นฐาน</p>
    <ul>
      <li>เพศ: {{ general.gender }}</li>
      <li>น้ำหนัก: {{ general.height }} KG</li>
      <li>ส่วนสูง: {{ general.weight }} CM</li>
      <li>โรคประจำตัว: {{ general.status }}</li>
    </ul>
    <button @click="showData()">คลิกเพื่อดูข้อมูล</button>
    <button @click="incressment(10)">เพิ่ม</button>
    <button @click="decressment(10)">ลด</button>
  </section>
</template>

<script>
export default {
  name: 'App',
  data() {
    return{
      firstname: "PPP",
      lastname: "zzz",
      age: 20,
      address: "<strong>กรุงเทพฯ</strong>",
      picture: "https://uxwing.com/wp-content/themes/uxwing/download/peoples-avatars/corporate-user-icon.png",
      size: 150,
      social: "https://ppppp.com",
      hobby: [
        "ทำสวน", "เล่นเกม", "ฟังเพลง"
      ],
      general: {
        gender: "ชาย", 
        weight: 80, 
        height: 170, 
        status: false
      }
    }
  },
  methods: {
    getFullName(){
      return this.firstname + " " + this.lastname
    },
    showData(){
      alert(this.firstname)
    },
    incressment(value){
      this.age += value;
    },
    decressment(value){
      this.age -= value;
    }
  }
}
</script>

<style></style>
