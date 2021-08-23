<template>
  <div>
    <h1>ข้อมูลทหาร</h1>
    <p>id: {{ userId }}</p>
    <p>เลขบัตรประจำตัวประชาชน: {{user.code}}</p>
    <p>ชื่อ - นามสกุล {{ user.name }} - {{ user.lastname }}</p>
    <p>ยศตำแหน่ง: {{user.rank}}</p>
    <p>email: {{ user.email }}</p>
    <p>password: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>