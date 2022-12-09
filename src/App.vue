<template>
  <h1>IronContacts</h1>
  <button @click="addContact()" type="button">Add Random Contact</button>
  <table>
        <thead>
          <tr>
            <th>Picture</th>
            <th>Name</th>
            <th>Popularity</th>
            <th>Won Oscar</th>
            <th>Won Emmy</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(contact, index) of contacts" :key="index">
            <!--<td>{{ index }}</td>-->
            <td><img :src="contact.pictureUrl" :alt="contact.name" width="70" /></td>
            <td>{{ contact.name }}</td>
            <td>{{ contact.popularity }}</td>
            <td>{{ won(contact.wonOscar) }}</td>
            <td>{{ won(contact.wonEmmy) }}</td>
          </tr>
        </tbody>
  </table>
</template>

<script>
import CONTACTS from "./contacts.json";

export default {
  data() {
    return {
      contacts: CONTACTS.slice(0,5),
    };
  },
  methods: {
    won(data) {
      if (data) {
        return "YES"
      }
      else return "NO"
    },
    addContact() {
      this.contacts.push(CONTACTS[Math.ceil(Math.random()*CONTACTS.length)])      
    },
  },  
}


</script>

<style>
</style>