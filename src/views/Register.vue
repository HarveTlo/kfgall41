<template>
  <div class="container">
    <table class="table table-striped table-bordered">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Role</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{user.firstName}} {{user.lastName}}</td>
                    <td>{{user.email}}</td>
                    <td>{{user.role}}</td>
                </tr>
            </tbody>
        </table>
  </div>
</template>
 
<script>
export default {};
</script>

<style scoped>
</style>