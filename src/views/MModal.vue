<template>
    <div class="box">
        <div class="form">
            <div style="position:relative;">
                <div class="close" @click="onClose">Close</div>
            </div>
            <p>First <input type="text" name="" v-model="user.first"></p>
            <p>Last<input type="text" name="" v-model="user.last"></p>
            <p>Email<input type="text" name="" v-model="user.email"></p>
            <p>Phone<input type="text" name="" v-model="user.phone"></p>
            <p>Location<input type="text" name="" v-model="user.location"></p>
            <hr />
            <button>Update User</button>
        </div>
    </div>
</template>
<script setup>
import { ref, defineEmits, defineProps, onMounted } from 'vue'

const emits = defineEmits(['onClose'])

const onClose = () => emits('onClose')

const props = defineProps({
  editUser: {
    type: Object,
    default: () => {}
  }
})

const user = ref({
  id: '',
  first: '',
  last: '',
  email: '',
  phone: '',
  location: ''
})

onMounted(() => {
  user.value = props.editUser
  console.log(user.value)
})
</script>
<style scoped>
.form {
    background-color: burlywood;
    border-radius: 1rem;
    padding: 10px;
    max-width: 300px;
    max-height: 300px;
}

.box {
    position: fixed;
    width: 100%;
    height: 100%;
    background-color: rgba(000, 000, 000, 0.8);
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    /* Centers horizontally */
    align-items: center;
    /* Centers vertically */
}

.close {
    cursor: pointer;
    position: absolute;
    right: -50px;
    top: -50px;
    background: red;
    border-radius: 50%;
    color: white;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    /* Centers horizontally */
    align-items: center;
    /* Centers vertically */
}
</style>
