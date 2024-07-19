<template>
  <table cellpadding="10" cellspacing="10" border="1">
    <thead>
      <tr>
        <th>ID</th>
        <th>First</th>
        <th>Last</th>
        <th>Email</th>
        <th>Phone</th>
        <th>Location</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(user, index) in users" :key="index">
        <td>{{ user.id }}</td>
        <td>{{ user.first }}</td>
        <td>{{ user.last }}</td>
        <td>{{ user.email }}</td>
        <td>{{ user.phone }}</td>
        <td>{{ user.location }}</td>
        <td>
          <button @click="edit(user)">Edit</button>
          <button>Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
  <MModal v-if="isEdit" @onClose="isEdit = false" :editUser="user"/>
  <!-- Form edit -->
</template>

<script setup>
import { reactive, ref } from 'vue'
import MModal from './views/MModal.vue'

const isEdit = ref(false)
const user = ref()
const users = reactive([
  {
    id: '0001',
    first: 'E',
    last: 'School',
    email: 'eschool@cambodia.com',
    phone: '098909761',
    location: 'Phnom Penh'
  },
  {
    id: '0001',
    first: 'E',
    last: 'School',
    email: 'eschool@cambodia.com',
    phone: '098909761',
    location: 'Phnom Penh'
  },
  {
    id: '0002',
    first: 'John',
    last: 'Doe',
    email: 'johndoe@example.com',
    phone: '098909762',
    location: 'Siem Reap'
  },
  {
    id: '0003',
    first: 'Jane',
    last: 'Smith',
    email: 'janesmith@example.com',
    phone: '098909763',
    location: 'Battambang'
  },
  {
    id: '0004',
    first: 'Alice',
    last: 'Johnson',
    email: 'alicejohnson@example.com',
    phone: '098909764',
    location: 'Sihanoukville'
  },
  {
    id: '0005',
    first: 'Bob',
    last: 'Brown',
    email: 'bobbrown@example.com',
    phone: '098909765',
    location: 'Kampong Cham'
  },
  {
    id: '0006',
    first: 'Charlie',
    last: 'Davis',
    email: 'charliedavis@example.com',
    phone: '098909766',
    location: 'Kampot'
  },
  {
    id: '0007',
    first: 'David',
    last: 'Wilson',
    email: 'davidwilson@example.com',
    phone: '098909767',
    location: 'Takeo'
  },
  {
    id: '0008',
    first: 'Ella',
    last: 'Martinez',
    email: 'ellamartinez@example.com',
    phone: '098909768',
    location: 'Kandal'
  },
  {
    id: '0009',
    first: 'Frank',
    last: 'Miller',
    email: 'frankmiller@example.com',
    phone: '098909769',
    location: 'Pursat'
  },
  {
    id: '0010',
    first: 'Grace',
    last: 'Garcia',
    email: 'gracegarcia@example.com',
    phone: '098909770',
    location: 'Koh Kong'
  }
])

const edit = (currentUser) => {
  isEdit.value = true
  user.value = currentUser
}
</script>
