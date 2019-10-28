<template>
  <b-row>
    <b-col cols="12" xl="6">
      <transition name="slide">
      <b-card>
        <div slot="header" v-html="caption"></div>
        <b-table :hover="hover" :striped="striped" :bordered="bordered" :small="small" :fixed="fixed" responsive="sm" :items="items" :fields="fields" :current-page="currentPage" :per-page="perPage" @row-clicked="rowClicked">
          <template slot="id" slot-scope="data">
            <strong>{{data.item.id}}</strong>
          </template>
          <template slot="name" slot-scope="data">
            <strong>{{data.item.name}}</strong>
          </template>
        </b-table>
        <nav>
          <b-pagination size="sm" :total-rows="getRowCount(items)" :per-page="perPage" v-model="currentPage" prev-text="Prev" next-text="Next" hide-goto-end-buttons/>
        </nav>
      </b-card>
      </transition>
    </b-col>
  </b-row>
</template>

<script>
import departmentData from './DepartmentData'
export default {
  name: 'Departments',
  props: {
    caption: {
      type: String,
      default: 'Departments'
    },
    hover: {
      type: Boolean,
      default: true
    },
    striped: {
      type: Boolean,
      default: true
    },
    bordered: {
      type: Boolean,
      default: false
    },
    small: {
      type: Boolean,
      default: false
    },
    fixed: {
      type: Boolean,
      default: false
    }
  },
  data: () => {
    return {
      items: departmentData.filter((department) => department.id < 8),
      fields: [
        {key: 'id'},
        {key: 'name'},
        {key: 'number'},
        {key: 'employees'}
      ],
      currentPage: 1,
      perPage: 2,
      totalRows: 0
    }
  },
  computed: {
  },
  methods: {
    // getBadge (status) {
    //   return status === 'Active' ? 'success'
    //     : status === 'Inactive' ? 'secondary'
    //       : status === 'Pending' ? 'warning'
    //         : status === 'Banned' ? 'danger' : 'primary'
    // },
    getRowCount (items) {
      return items.length
    },
    departmentLink (id) {
      return `departments/${id.toString()}`
    },
    rowClicked (item) {
      const departmentLink = this.departmentLink(item.id)
      this.$router.push({path: departmentLink})
    }

  }
}
</script>

<style scoped>
.card-body >>> table > tbody > tr > td {
  cursor: pointer;
}
</style>
