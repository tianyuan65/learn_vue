// 名为Firm的单文件组件
<template>
    <!--组件的结构  -->
    <div  class="demo">
        <h2>公司名称：{{firmName}}</h2>
        <h2>公司地址：{{address}}</h2>
        <button @click="showName">click to show firm name</button>
    </div>
</template>

<script>
    // 组件交互相关的代码(数据、方法等)
    // const Firm=Vue.extend({
    //     data(){
    //         return {
    //             firmName:'729声工场',
    //             address:'北京市朝阳区'
    //         }
    //     },
    //     methods:{
    //         showName(){
    //             alert(this.showName)
    //         }
    //     }
    // })
    // // 默认暴露
    // export default Firm

    // 默认暴露，并简写版，不写Vue.extend方法
    export default {
        // name配置项，添加组件名
        name:'Firm',
        // 数据
        data(){
            return {
                firmName:'729声工场',
                address:'北京市朝阳区'
            }
        },
        // methods
        methods:{
            showName(){
                alert(this.showName)
            }
        }
    }
</script>

<style>
    /* 组件的样式 */
    .demo{
        background-color: #bfa;
    }
</style>