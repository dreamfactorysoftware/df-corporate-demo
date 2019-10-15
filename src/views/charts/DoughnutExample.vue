<script>
import { Doughnut } from 'vue-chartjs'
import axios from 'axios'

export default {
  extends: Doughnut,
// getData () {
//     axios.get('https://demo.dreamfactory.com/api/v2/df-corporate-demo/_table/departments?related=*&api_key=00218f67950a34f3f4d6127c57369dc935246c3194d5902e3e00e251f0dabf59')
//       .then((response) => {
//         console.log("here")
// console.log(response.data.resource[0].dept_name)
// labels.push([response.data.resource[0].dept_name]) 
//       })
//   },
  mounted () {
    var labels = []
    axios
      .get('https://demo.dreamfactory.com/api/v2/df-corporate-demo/_table/departments?related=*&api_key=00218f67950a34f3f4d6127c57369dc935246c3194d5902e3e00e251f0dabf59')
      .then(response => console.log(response.data.resource))
    this.renderChart({
      labels: ['VueJs', 'Ember', 'ReactJs', 'AngularJs'],
      datasets: [
        {
          backgroundColor: [
            '#41B883',
            '#E46651',
            '#00D8FF',
            '#DD1B16'
          ],
          data: [40, 20, 80, 10]
        }
      ]
    }, {responsive: true, maintainAspectRatio: true})
  }
}
</script>
