<template>
  <b-row>
    <b-col cols="12" lg="6">
      <b-card no-header>
        <template slot="header">
          Department id:  {{ $route.params.id }}
        </template>
        <b-table striped small fixed responsive="sm" :items="items($route.params.id)" :fields="fields">
          <template slot="value" slot-scope="data">
            <strong>{{data.item.value}}</strong>
          </template>
        </b-table>
        <template slot="footer">
          <b-button @click="goBack">Back</b-button>
        </template>
      </b-card>
    </b-col>
  </b-row>
</template>

<script>
import departmentData from './DepartmentData'
export default {
  name: 'Department',
  props: {
    caption: {
      type: String,
      default: 'Department id'
    },
  },
  data: () => {
    return {
      items: (id) => {
        const department = departmentData.find( department => department.id.toString() === id)
        const departmentDetails = department ? Object.entries(department) : [['id', 'Not found']]
        return departmentDetails.map(([key, value]) => {return {key: key, value: value}})
      },
      fields: [
        {key: 'key'},
        {key: 'value'},
      ],
    }
  },
  methods: {
    goBack() {
      this.$router.go(-1)
      // this.$router.replace({path: '/users'})
    }
  }
}
</script>
