<template>
  <div>
    <firm></firm>
    <staff></staff>
  </div>
</template>

<script>
    // 引入组件
    import Firm from './Firm.vue'
    import Staff from './Staff.vue'

    export default {
        name:'App',
        components:{
            Firm,
            Staff
        }
    }
</script>

