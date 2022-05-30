<template>
  <div id="app">
    <img alt="Vue logo" src="https://vuejs.org/images/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <button @click="fetchAPIData()">FetchAPICustomers</button>
    <table class="container" border="yes">
      <tr>
        <th>CustomerID</th>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
        <th>Phone_Number</th>
        <th>Country Code</th>
        <th>Gender</th>
        <th>Balance</th>
        <th></th>
        <th></th>
      </tr>

      <!-- loop here -->
      <tr>
        <td>{{ CustomerID }}</td>
        <td>{{ Firstname }}</td>
        <td>{{ Lastname }}</td>
        <td>{{ Email }}</td>
        <td>{{ Phone_Number }}</td>
        <td>{{ Country_Code }}</td>
        <td>{{ Gender }}</td>
        <td>{{ Balance }}</td>
        <td><button type="button" class="btn btn-danger">delete</button></td>
        <td><button type="button" class="btn btn-primary">edit</button></td>
      </tr>
      <!-- end -->
    </table>

    <div class="container">
      <b>Create or Edit a Customer</b> <br />
      <label>Firstname: </label>
      <input placeholder="Firstname" class="form-control" /> <br />
      <label>Lastname: </label>
      <input placeholder="Lastname" class="form-control" /> <br />
      <label>Email: </label>
      <input placeholder="Email" class="form-control" /> <br />
      <label>Phone_Number:</label>
      <input placeholder="Phone_Number" class="form-control" /> <br />
      <label>Country_Code:</label>
      <input placeholder="Country_Code" class="form-control" /> <br />
      <label>Gender: </label>
      <input placeholder="Gender" class="form-control" /> <br />
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  /*props: {
    CustomerID: String,
    Firstname: String,
    Lastname: String,
    Email: String,
    Phone_Number: String,
    Country_Code: String,
    Gender: String,
    Balance: String,
  },*/
  data() {
    return {
      CustomerID: '191827fh',
      Firstname: 'Nathaniel',
      Lastname: 'Burman',
      Email: 'EMail@email.com',
      Phone_Number: '123456789',
      Country_Code: 'US',
      Gender: 'Male',
      Balance: '0',
    };
  },
  methods: {
    toggleBox() {
      console.log('test');
    },
    // get customers
    fetchAPIData() {
      axios
        .get('https://getinvoices.azurewebsites.net/api/Customers')
        .then((response) => {
          // JSON responses are
          // automatically parsed
          this.posts = response.data;
        })

        // Dealing with errors
        .catch((error) => {
          console.log(error);
          this.errored = true;
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
