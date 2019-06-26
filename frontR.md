## Vue前端开发代码规范

### Vue

1. 组件名
   - 自定义组件名为多个单词时，应使用连接线（-）连接，避免与HTML标签冲突，使结构更加清晰；当使用单个单词为组件名时，应遵循首字母大写的原则；
  
    		<div>
    		<S-Identify :identifyCode="identifyCode2" @click.native="refreshCode" style="margin-top:15px;float:right;"></S-Identify>
    		</div>

2. 组件文件
   - 组件与布局文件遵循首字母大写原则，当为多个单词组成的复合结构时，每个单词均应大写表示，不使用符号连接；
   
			├── index.html
			├── main.js
			├── api
			│   └── ...
			├── Views
			│   ├── Personal.vue
			│   ├── Account.vue
			│   ├── CreateQues.vue
			│   ├── FillingQues.vue			
			│   └── ...
			├── store
			│	└── ...    
			└── ...     
3. data
   - data中的数据应始终使用函数的方法，即return
   
		    data() {
		        return {
		            detailModel: false,
		            index: 0
		        }
	    	}

4. prop
   - 定义prop变量时应尊重JavaCript的语言特性，使用驼峰命名法
   - 定义prop时应详细指出其类型、作用、验证等信息；
   
			props: {
			  status: {
			    type: String,
			    required: true,
			    validator: function (value) {
			      return [
			        'syncing',
			        'synced',
			        'version-conflict',
			        'error'
			      ].indexOf(value) !== -1
			    }
			  }
			}

5. compute
   - 计算属性统一使用 name: function(){}的模式编写
   			
			//普通计算属性
			computed: {
			  finalPrice: function () {
			    return this.basePrice - this.discount
			  }
			}
			//mapState
			computed: mapState('Personal', {
		        publishLists: 'publishing',
		        attendLists: 'attending',
		        collectLists: 'starring',
		        detailContent: 'quesDetail'
		    }),


6. v-for
   - 使用v-for遍历时应声明索引值，提高渲染效率
   
			 <div v-for="(ques,index) in sortPublished">
		                    <div>
		                        <span id="dynamicDate" style="font-size:15px;color:#ce4545;vertical-align:middle;"> ● {{ques.Infos.createTime}} </span> <span style="font-size:15px;vertical-align:middle;color:gray;">我发布了</span>
		                    </div>
		                    <task :data="ques" :key="index" type="1" mode="0" @click.native="getDetail(ques.quesID)"></task>
		                </div>


7. v-if
   - 使用v-if渲染时应使用v-else进行完全的逻辑判断与渲染，避免发生歧义
   
			<div
			  v-if="error"
			  key="search-status"
			>
			  错误：{{ error }}
			</div>
			<div
			  v-else
			  key="search-results"
			>
			  {{ results }}
			</div>


8. 缩写
   - v-bind统一使用：代替
   - v-on统一使用@代替


 		<task :data="ques" :key="index" type="1" mode="0" @click.native="getDetail(ques.quesID)"></task>

9. 样式
   - style标签统一使用scoped特性约束
   - 对于iview组件库自带样式的修改，统一使用!important方法进行覆盖
 

			<style scoped>
			#grad {
			    background: linear-gradient(to right, #FF6699, #FF4B3C);
			}
			
			.showPage {
			    .ivu-btn-info {
			        color: #fff;
			        background-color: rgba(255, 255, 255, 0) !important;
			        border-color: #fff !important;
			    }
			
			    .ivu-btn-info span {
			        font-size: 24px !important;
			    }
				...
			}
			</style>


10. 元素顺序
    - 单文件统一按照`<template><script><style>`的顺序进行编写


### JavaScript

1. 变量声明
   - 循环变量尽量在循环语句中声明，特殊情况除外，声明时应赋初值
   - 不再使用var进行变量声明，而是使用let/const
   
        create() {
            let info = JSON.parse(window.sessionStorage.getItem('LogInfo'))
            if (info.log)
                this.$router.push({ name: 'createQuestionnaire' })
            else
                this.$Message.warning('您还未登录，请先登录后发布问卷。')
        }


2. 引号
   - 不使用双引号标注字符串，统一使用单引号，以便处理大量中文字符串中含有双引号的问题
  

			setInformation(i, t) {
	            if (t == 1) {
	                this.info = '关闭问卷将不会回收到该问卷且无法重新开启，确认关闭问卷？（未使用押金会退回到您的账户）'
	            } else {
	                this.info = '删除问卷将无法到该问卷相关信息，确认删除问卷？（未使用押金会退回到您的账户）'
	
	            }
	            this.id = i
	            this.type = t
	        }

3. 函数
   - 统一使用箭头函数
   - 多个值作为返回值或参数时，统一使用data的JSON结构进行封装后传入函数或进行返回
   - 函数名使用驼峰命名法

	        checkIndentify() {
	            var userMode = this.checkValid(this.info.username)
	            if (userMode !== 'invalid') {
	                this.info.mode = this.checkValid(this.info.username)
	                this.$store.dispatch('CHECK_IDENTIFY', this.info).then(
	                    (response) => {
	                        console.log(response)
	                        if (response['success']) {
	                            alert("Your verify done!")
	                        }
	                    }
	                )
	            }
	        }

4. 模块
   - 使用import/export方法统一进行模块管理
   - import放在js结构顶部
   - 当只有一个export值时，使用export default方法

			<script>
			import SIdentify from "./components/IdentifyFromLocal"
			import SIdentify1 from "./components/IdentifyFromAPI"
			import { Personal } from '../store/personal/index.js'
			import { mapState } from 'vuex'
			import { mapGetters } from 'vuex'
			export default {
			   ...
			}
			</script>


5. 循环
   - 使用for(var i=0, j=arr.length; i<j; ++i)的格式进行循环

			export default {
			    [GET_INFO]({ commit }) {
			        return personalAPI.getPersonalInfo().then((info) => {
			            commit(mutations.SET_PER_INFO, info.data)
			        })
			    },
			    [UPDATE_INFO]({ state, commit }) {
			        let data = state.personalInfo;
			        console.log("data in actions:" + data);
			        personalAPI.setPersonalInfo(data).then((info) => {
			            commit(mutations.SET_PER_INFO, data)
			        })
			    },
				...
			}




7. api
   - api编写应使用Promise原则，在函数头部编写注释生命参数
   - 统一返回response.data


			/**
			 * Reserved API for new user's registration.
			 * Register with a post to register url with the data {username, password}.
			 * @param {string} username The username of new user.
			 * Should be email or phone judged by frontend
			 * @param {string} password The password of new user.
			 * @param {string} mode The mode of new user.
			 * @return {Promise}
			 * Promise will return the json data with success and message
			 */
			export async function userRegister(username, password, mode) {
			    let data = {}
			    if (mode === 'phone')
			        data = { "phone": username, "password": password }
			    else
			        data = { "email": username, "password": password }
			    let response = await service.post('/register', data)
			    console.log(response.data)
			    return response.data
			}


### HTML/CSS

1. 标准
   - HTML5+CSS3

2. 选择器
   - 使用选择器时应用简略的声明，如.test 而非p.test
   - 尽量使用类选择器而非元素选择器

				let email = /^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\.[a-zA-Z0-9-]+)*\.[a-zA-Z0-9]{2,6}$/
                let phone = /^1[34578]\d{9}$/
                if (phone.test(username)) {
                    return 'phone'
                } else if (email.test(username)) {
                    return 'email'
                } else {
                    this.wrong = true
                    this.alert = '无效的用户名'
                    return 'invalid'
                }


3. 分号
   - 所有样式均应使用；结尾，最后一个声明也不例外


			#sendIndentify {
			    margin-top: 25px;
			    float: right;
			    color: #fff;
			    border-radius: 5px;
			    background-color: #3cb175;
			}



4. 样式
   - 简短（<5）的样式定义应使用内联样式进行定义，保证优先级的同时便于查看


                <div style=" text-align: center;">
                    <img src="../../static/noAttend.png" style="width:500px" />
                </div>

