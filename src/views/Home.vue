<template>
   <div>
     <div>
          <button v-on:click="byGender()" :class="{active: isActive('A')}">gender-lastname asc</button>
          <button v-on:click="byDate()" :class="{active: isActive('B')}">date asc</button>
          <button v-on:click="byLastName()" :class="{active: isActive('C')}">lastname desc</button>        
     </div>
      <table>
        <tr>
          <th>Last Name</th>
          <th>First Name</th>
          <th>Registered</th>
          <th>Gender</th>
           <th>Color</th>
        </tr>
        <tr v-for="user in users" v-bind:key="user.firstname">
          <td>{{ user.lastname }}</td>
          <td>{{ user.firstname }}</td>
          <td>{{ user.registered }}</td>
          <td>{{ user.gender }}</td>
          <td>{{ user.color }}</td>
        </tr>
      </table>
    </div>
</template>

<script>
export default {
    data() {
      return {
        active: 'A',
        users:[
          {"firstname": "Martina", "lastname": "Hingis", "gender": "Female", "registered": "4/2/1979", "color": "Green"},
          {"firstname": "Sue", "lastname": "Kelly", "gender": "Female", "registered": "7/12/1959", "color": "Pink"},
          {"firstname": "Neil", "lastname": "Abercrombie", "gender": "Male", "registered": "2/13/1943", "color": "Tan"},
          { "firstname": "Ana", "lastname": "Kournikova", "gender": "Female", "registered": "6/3/1975", "color": "Red"},
          {"firstname": "Timothy", "lastname": "Bishop", "gender": "Male", "registered": "4/23/1967", "color": "Yellow"},
          {"firstname": "Monica", "lastname": "Seles", "gender": "Female", "registered": "12/2/1973", "color": "Black"},
          {"firstname": "Radek", "lastname": "Bonk", "gender": "Male", "registered": "6/3/1975", "color": "Green"},
          {"firstname": "Francis", "lastname": "Bouillon", "gender": "Male", "registered": "6/3/1975", "color": "Blue"},
          {"firstname": "Steve", "lastname": "Smith", "gender": "Male", "registered": "3/3/1985", "color": "Red"},
       ]
      }
    },
    methods: {
       byDate() {
          this.users.sort((a, b) => 
               new Date(a.registered) - new Date(b.registered)   
          );
          this.active = 'B';
        },
        byGender() {
          this.users.sort((a,b) =>  a.lastname < b.lastname ? -1 : 1);
          this.users.sort((a,b) =>  a.gender < b.gender ? -1 : 1);
          this.active = 'A';
        },
        byLastName() {
          this.users.sort((a,b) =>  a.lastname < b.lastname ? 1 : -1);
          this.active = 'C';
        },
        isActive(value) {
          return this.active === value;
        }
    } 
}
</script>

<style lang="scss" scoped>
table {
  padding: 20px;
  td {
    padding: 10px;
  }
}
.active {
  background-color: red;
}

</style>

