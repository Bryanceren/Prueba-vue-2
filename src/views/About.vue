<template>
   <v-simple-table>
      <thead>
        <tr>
          <th class="text-left">
            transparency
          </th>
          <th class="text-left">
            prec type
          </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{ this.$route.query.transparency}}</td>
          <td>{{ this.$route.query.type }}</td>
        </tr>
      </tbody>
  </v-simple-table>
    
  
</template>

<script>
export default {
  setup() {
    
  },
}
</script>
