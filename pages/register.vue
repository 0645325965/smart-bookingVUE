<template>
  <v-parallax src="/pic/background.png" height="643">
    <v-layout>
      <v-flex xs12 lg6>
        <h1>Register Member.</h1>
        <v-text-field v-model="user" label="อีเมลล์" dark />
        <v-text-field v-model="pass" label="รหัสผ่าน" dark />
        <v-text-field v-model="first_name" label="ชื่อผู้ใช้" dark />
        <v-text-field v-model="last_name" label="นามสกุล" dark />
        <v-btn color="success" @click="save">บันทึก</v-btn>
    </v-flex></v-layout>
  </v-parallax>
</template>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
<script>
export default {
  data() {
    return {
      user: '',
      pass: '',
      first_name: '',
      last_name: '',
    }
  },
  methods: {
    async save() {
      let res = await this.$http.post('/student/regis', {
        user: this.user,
        pass: this.pass,
        first_name: this.first_name,
        last_name: this.last_name,

      })
      if (!res.data.ok) {
        // TODO: แสดงข้อความ ว่าบันทึกไม่สำเร็จ
      } else {
        // TODO: แสดงข้อความ ว่าบันทึกสำเร็จ
        this.$router.push('/login')
      }
    },
  },
}
</script>
