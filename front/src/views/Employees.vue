<template>
<div>
  <GetListEmployee/>
  <PostEmployees/>
</div>
</template>

<script>
import GetListEmployee from '@/components/Employees/GetListEmployee.vue'
import PostEmployees from '@/components/Employees/PostEmployees.vue'

export default {
components : {
  GetListEmployee,
  PostEmployees
  }
}
</script>

<style>

</style>
