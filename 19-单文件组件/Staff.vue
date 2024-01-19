// 名为Staff的单文件组件
<template>
    <!--组件的结构  -->
    <div  class="demo">
        <h2>员工姓名：{{staffName}}</h2>
        <h2>员工年龄：{{age}}</h2>
    </div>
</template>

<script>
    // 组件交互相关的代码(数据、方法等)
    // const Staff=Vue.extend({
    //     data(){
    //         return {
    //             staffName:'谷江山',
    //             age:29
    //         }
    //     }
    // })
    // // 默认暴露
    // export default Staff

    // 默认暴露，并简写版，不写Vue.extend方法
    export default {
        // name配置项，添加组件名
        name:'Staff',
        // 数据
        data(){
            return {
                staffName:'谷江山',
                age:29
            }
        }
    }
</script>

<style>
    /* 组件的样式 */
    .demo{
        background-color: #ccf;
    }
</style>