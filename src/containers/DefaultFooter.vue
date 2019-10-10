<template>
      <TheFooter>
        <div>
          <!--footer-->
          <a href="https://genie.dreamfactory.com/">Start your free trial!</a>
        </div>
        <div class="ml-auto">
          <span class="mr-1">Powered by</span>
          <a href="https://www.dreamfactory.com/">DreamFactory</a>
        </div>
      </TheFooter>
</template>
<script>
import { Footer as TheFooter } from '@coreui/vue'
export default {
  name: 'DefaultFooter',
  components: {
    TheFooter
  },
}
</script>
