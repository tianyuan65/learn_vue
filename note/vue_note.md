## VUE
* **VUE**
    * 什么是VUE？
        * 是一套用于构建用户界面的渐进式JavaScript框架，简单来说就是程序员把数据通过一系列操作(VUE)，变成用户看见的界面。前端开发工程师的职责：在合适的时候，发出合适的请求，把数据展示到合适的位置。
            * 渐进式：VUE可以自底向上逐层地应用，简单应用，只需引入一个100kb的轻量小巧的核心库；复杂应用的话可以引入各式各样的VUE插件。也就是逐渐从轻量小巧的核心库递进到使用各式各样的Vue插件库。
    * 谁开发的？
        * 尤雨溪 2013 Vue V0.60-2022 VUE V3.x
    * VUE的特点
        * 1. 采用组件化模式，提高代码复用率，且让代码更好维护。一个vue一个组件，可以把自己喜欢的vue文件引入过来，并直接使用，若想要修改某个部分的布局，就直接修改该vue文件的HTML结构即可，不会影响相邻的模块。
            * ![一个vue文件，就代表一个组件](images/一个vue一个组件.png)
        * 2. 声明式编码，让编码人员无需直接操作DOM，提高开发效率。JS的命令式编码->VUE的声明式编码
        * 3. 使用虚拟DOM + 优秀的Diffing算法，尽量复用DOM节点。将原始的虚拟DOM与新的虚拟DOM进行比较(这个比较就叫Diff)，用Diffing算法进行比较后，一样的直接复用，不一样的增删改。
        * 4. 学习VUE之前要掌握的JS基础知识
            * ES6语法规范：解构赋值，模板字符串，箭头函数等
            * ES6模块化：默认/分别/统一暴露，import，export等
            * 包管理器：npm，yarn，cnpm等
            * 原型、原型链
            * 数组常用方法：过滤/加工数组，筛选最值等
            * axios：async await
            * promise...
    
* **第一章 Vue核心**
    * 1.1 Vue简介
        * 1.1.1 官网
            * 1. 英文官网: https://vuejs.org/
            * 2. 中文官网: https://cn.vuejs.org/
        * 1.1.2 介绍与描述
            * 1. 动态构建用户界面的渐进式 JavaScript 框架
            * 2. 作者：尤玉溪
        * 1.1.3 Vue的特点：
            * 1. 遵循MVVM模式
            * 2. 编码简介，体积小，运行效率高，适合移动端/PC端
            * 3. 它本身只关注 UI, 也可以引入其它第三方库开发项目
        * 1.1.4 与其他JS框架的关联
            * 1. 借鉴Angular的模板和数据绑定技术
            * 2. 借鉴React的组件化和虚拟DOM技术
        * 1.1.5 Vue周边库
            * 1. vue-cli：vue脚手架
            * 2. vue-resource
            * 3. axios
            * 4. vue-router：路由
            * 5. vuex：状态管理
            * 6. elemnt-ui：给予vue的UI组件库(PC端)
    * 1.2 初识Vue
        * ```
            <!-- 准备一个容器 -->
            <div id="root">
                <h1>hello，尚硅谷！</h1>
            </div>
          ```
        * ![hello,尚硅谷！](images/hello,shangguigu.png)
        * 创建Vue实例，Vue实例化传且只传一个参数，并且类型是一个对象，管这种对象叫配置对象。像axios，传递的参数也是配置对象，配置对象的key值和value值都有要求，要用指定的，不能乱写，Vue的配置对象也一样。配置对象内的数据，只供与实例绑定的容器使用，以外的管不着。
            * 1. 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象
            * 2. root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法
                * ```<div id="root"><h1>Hello,{{name}}</h1></div>```中，{{name}}就是特殊语法
            * 3. root容器的代码被称为【Vue模板】
            * ```
                <!-- 创建Vue实例 -->
                const v=new Vue({
                    // 与容器建立关系，el用于制订单那个钱Vue实例为哪个容器服务，值通常为css选择器字符串, 
                    // el:'#root'，也可以写成el:document.getElementById('root')
                    el:'#root',
                    data:{ //data中用于存储数据，数据供el指定的容器使用，值先写成一个对象
                        name:'尚硅谷',
                    }
                })
              ```
            * 4. 一个Vue实例不能同时接管两个容器，Vue实例和容器是一一对应的关系。
                * ```
                    <!-- 准备一个容器 -->
                    <div id="root">
                        <h1>Hello,{{name}},{{address}}</h1>
                    </div>
                    <div id="root2">
                        <h1>Hello,{{name}},{{address}}</h1>
                    </div>
                    <script type="text/javascript">
                        Vue.config.productionTip=false  //组织vue在启动时生成生产提示。

                        // 创建Vue实例
                        new Vue({
                            // 与容器建立关系,el用于制订单那个钱Vue实例为哪个容器服务,值通常为css选择器字符串, 
                            // el:'#root',也可以写成el:document.getElementById('root')
                            el:'#root',
                            data:{ //data中用于存储数据，数据供el指定的容器使用，值先写成一个对象
                                name:'尚硅谷',
                                address:'深圳'
                            }
                        })
                        new Vue({
                            el:'#root2',
                            data:{
                                name:'atguigu',
                                address:'北京昌平'
                            }
                        })
                  ```
                * ![Vue实例和容器是一一对应的关系，不能一个Vue实例对多个容器或多个Vue实例对一个容器](images/一个萝卜，一个坑，一个Vue实例对应一个容器.png)
            * 5. 真实开发中只有一个Vue实例，并且会配合着组件一起使用。
            * 6. 写在容器里的{{xxx}}里的代码必须写JS表达式，且xxx可以自动读取到data中的所有属性。
            * 7. 一旦data中的数据发生改变，页面中用到该数据的地方也会自动更新
                    * ![根组件，鼠标悬停在data的属性的值上还可以修改其值](images/打开vue的开发者工具后展示的根组件.png)
    * 1.3 模板语法
        * 1.3.1 效果
            * ![插值语法和指令语法效果](images/插值和指令语法.png)
        * 1.3.2 模板的理解，html中包含一些JS语法代码，语法分为两种，分别为：
            * 1. 插值语法(双大括号表达式)
            * 2. 指令语法(以 v- 开头)，用于管理标签属性
        * 1.3.3 插值语法
            * 1. 功能：用于解析/指定标签体内容
            * 2. 语法：{{xxx}}，xxx会作为js表达式解析，且可以直接读取到data中的所有属性
        * 1.3.4 指令语法
            * 1. 功能：用于解析/管理标签(包括标签属性、标签体内容、绑定事件...)
            * 2. 举例：v-bind:href="xxx" 或 简写为 :href="xxx"，xxx同样要写js表达式，且可以直接读取到data中的所有属性。
            * 3. 备注：Vue中有很多指令，且形式都是：v-???，在这里先学v-bind
    * 1.4 数据绑定
        * 1.4.1 效果
        * 1.4.2 单向数据绑定
            * 1. 语法：v-bind:href="xxx" 或简写为 :href
            * 2. 特点：数据只能从data流向页面
                * ![数据从data流向页面](images/单向数据绑定_data到page.png)
        * 1.4.3 双向数据绑定
            * 1. 语法：v-model:value="xxx" 或简写为 v-model="xxx"
            * 2. 特点：数据不仅能从data流向页面，还能从页面流向data
                * ![数据会从页面流向data，但因data中数据变化，单向的那条线也会动作](images/双向绑定.png)
            * 3. 备注：
                * 双向绑定一般都应用在都应用在表单类元素上(如，input、select等)。
                * v-model:value 可以简写为 v-medel，因为v-medel默认收集的就是value值。
                * 如下类代码是错误的，因为v-model只能应用在表单类/输入类元素上，因为标题类标签无法捕获用户的输入，有value标签属性的就叫输入类元素。
                * ```<h2 v-model:x="name">hi</h2>```
    * 1.5 el和data的两种写法
        * 1.5.1 el的两种写法
            * 1. new Vue的时候配置el属性
            * 2. 先创建Vue实例，随后再通过vm.$mount('#root)指定el的值。
        * 1.5.2 data的两种写法
            * 1. 对象式
            * 2. 函数式
            * 选哪个？ 目前是哪个都行，以后学到组件的时候，必须写函数式，要不然出事儿
        * **1.5.3 一个重要原则**
            * 由Vue管理的函数，一定不能写箭头函数，必须是普通函数，一旦写了箭头函数，this指向的就不是Vue实例了，而是Window，且data函数也可以简写成```data(){....}```
                * ```
                    data:function(){
                        console.log('data',this);  //此处的this是Vue实例对象
                        return{
                            name:'谷江山'
                        }
                    }
                  ```
    * 1.6 MVVM模型
        * 1. M：模型(Model)：对应data中的数据
        * 2. V:视图(View)：模板
        * 3. VM：视图模型(ViewModel)：Vue实例对象
            * ![模型盒子版](images/MVVM模型盒子版.png)
            * ![模型代码实现版](images/MVVM模型代码实现版.png)
        * 观察发现：
            * 1. data中所有的属性，最后都出现在了vm身上
            * 2. vm身上是所有的属性 及 Vue原型上所有属性，在Vue模板中都可以直接使用
    * 1.7 数据代理
        * 1.7.1 Vue中的数据代理：
            * 通过vm对象来代理data对象中熟悉宁德操作(读/写)
        * 1.7.2 Vue中数据代理的好处：
            * 更加方便地操作data中的数据
        * 1.7.3 基本原理
            * 通过Object.defineProperty方法把data对象中所有的属性添加到vm上。
            * 为每一个添加到vm上的属性，都制定一个getter/setter。
            * 在getter/setter内部去操作(读/写)，data中对应的属性。
            * ![数据代理图示](images/数据代理图示.png)
    * 1.8 事件处理
        * 1.8.1 

            
* **第二章 Vue组件化编程**
* **第三章 使用Vue脚手架**
* **第四章 Vue中的ajax**
* **第五章 vuex**
* **第六章 vue-router**
* **第七章 Vue UI组件库**