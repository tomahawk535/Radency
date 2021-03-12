<template>
  <div class="users-list">
    <p>Click the button to show users list</p>
    <input type="button" value="Import users" @click="show =  true">

    <table border='1' class="users-list-table"
    v-if="show">
      <thead>
        <tr>
          <th>num</th>
          <th
            v-for="header in list"
            :key="header.id"
            >{{header}}</th>
        </tr>
      </thead>
      <tbody>
          <tr v-for="person in personList"
              :key="person.id"
              >
            <td>{{personList.indexOf(person)+1}}</td>
            <td>{{Object.values(person)[0]}}</td>
            <td>{{Object.values(person)[1]}}</td>
            <td>{{Object.values(person)[2]}}</td>
            <td>{{Object.values(person)[3]}}</td>
            <td>{{Object.values(person)[4]}}</td>
            <td>{{Object.values(person)[5]}}</td>
            <td>{{Object.values(person)[6]}}</td>
            <td>{{Object.values(person)[7]}}</td>
            <td>{{Object.values(person)[8]}}</td>
            <td>{{Object.values(person)[9]}}</td>

          </tr>
      </tbody>
<!--        <td-->
<!--          v-for="info in person"-->
<!--        :key="info.id"-->
<!--        v-bind:class="{error: isError}"-->
<!--          @click="getAgeEr()">{{info}}</td>-->

    </table>
  </div>
</template>

<script>
export default {
name: "UsersList",

  data: function (){
    return{
      personList: {},
      list: null,
      isError: true,
      show: false

    }
  },
  watch: {

  },
  computed:{

  },
  methods: {

  },
  mounted() {
      let self = this;
      this.$papa.parse('./normal.csv', {
        download: true,
        header: true,
        complete: function (results) {
          console.log(results);
          self.personList = results.data;
          self.list = results.meta.fields;
        },
      });
  }
}
</script>

<style scoped>
.error {
  color: darkred;
}
input {
  color: #fff;
  background-color: #42b983;
  border-radius: 10px;
  outline: none;
  border: none;
  padding: 1rem;
  text-transform: uppercase;
  box-shadow: 0 0 10px rgba(66,185,131, 0.5);
}
input:hover {
  cursor: pointer;
}
table {
  width: 80%;
  margin: 1rem auto;

  text-align: left;
}
th {
 text-transform: uppercase;
  padding: .7rem;
}
td {
  padding: 0.7rem;
}
</style>