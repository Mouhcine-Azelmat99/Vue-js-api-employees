<template>
  <div class="main">
    <h1>employess listes</h1>
    <div class="search-box">
      <input type="text" class="form-control" v-model="search" placeholder="Search ...">
    </div>
    <table class="table table-hover bg-light">
      <thead>
        <tr>
          <th scope="col">id</th>
          <th scope="col">Name</th>
          <th scope="col">Salary</th>
          <th scope="col">Age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in filtreEmployee" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.employee_name }}</td>
          <td>{{ item.employee_salary }}</td>
          <td>{{ item.employee_age }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Employees",
  data() {
    return {
      employees: [],
      search:'',
    };
  },
  created() {
    axios
      .get("http://dummy.restapiexample.com/api/v1/employees")
      .then((res) => {
        // console.log(res.data.data);
        this.employees = res.data.data;
        console.log(this.employees);
        }
    );
  },
  computed:{
    filtreEmployee(){
      return this.employees.filter((empoloyee)=>{
        return empoloyee.employee_name.match(this.search)
      });
    }
  }
};
</script>

<style lang="scss">
.main {
  padding: 40px 20px;
  background: #eee;
  min-height: 100vh;
  h1 {
    background-color: #fff;
    padding: 20px;
    margin: 0 20px;
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    font-weight: bold;
    margin-bottom: 40px;
  }
  .search-box{
    margin: 20px;
    input{
      background: #fff;
      padding: 10px 20px;
      font-size: 1rem;
        font-weight: bold;
      &:focus{
        background: #dff9fb;
        box-shadow: none;
      }
      &::placeholder{
        font-size: 1rem;
        font-weight: bold;
      }
    }
  }
}
</style>
