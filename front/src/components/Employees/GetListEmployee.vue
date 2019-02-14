<template>
  <table id="employees">
    <thead>
      <tr>
        <th
          v-for="(prop, p) in employeeProps"
          :key="p"         
        >{{prop}}</th>
      </tr>
    </thead>
    <tbody>
         <tr v-for="(prop, p) in employees" :key="p">
            <td v-for="(s, n) in prop" :key="n">{{s}}</td> 
        </tr>
    </tbody>
  </table>
</template>
<script>
import axios from "axios";
const URL = "http://localhost:8181/employee/getAll";
export default {
  created() {
    this.$store.dispatch("getEmployees");
  },
  mounted() {

  },
  data() {
    return {  };
  },
  computed: {
    employees(el) {
      console.log("chelouuuu", el);
      return this.$store.getters["employeeSecs"];
    },
    employeeProps() {
      return this.employees[0] ? Object.keys(this.employees[0]) : [];
    }
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
#employees {
  border-collapse: collapse;
  td,
  th {
    border: 1px solid;
    padding: 10px;
  }
}
</style>