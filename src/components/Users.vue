<template >
    <ul class="list-group mt-5">
        <li class="list-group-item list-group-item-action" v-for="user in userList" :key="user.id">
             <div class="d-flex w-100 justify-content-between">
                 <h3>{{user.name}}</h3>
                  <small class="text-danger delete" @click="deleteUser(user.id)">&#10005;</small>
             </div>
              <p>{{user.email}}</p>
        </li>
    </ul>
</template>
<script>
  import {
    mapGetters,
    mapActions
  } from "vuex";
export default {

    name:"Users",
     methods: {
      ...mapActions(["fetchUsers", "deleteUser"])
    },
   computed:mapGetters(["userList"]),
    created() {
      this.fetchUsers()
    }
}
</script>
<style>
 .delete {
   font-size: 18px;
   cursor: pointer;
 }
</style>