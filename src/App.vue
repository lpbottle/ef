<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import OptionsCourseContainer from './components/OptionsCourseContainer.vue'

// 是否显示级别菜单
let showOptions = ref(false)

// 显示/隐藏级别菜单
function changeLevel() {
    showOptions.value = !showOptions.value
}

const orderCourse = {
        name: '普通英语',
        list: [{
            title: '学习方法',
            passed: false,
            active: false
        }, {
            title: '1-入门级',
            passed: false,
            active: true
        }, {
            title: '2-入门级',
            passed: false,
            active: false
        }, {
            title: '3-入门级',
            passed: false,
            active: false
        }, {
            title: '4-初级',
            passed: true,
            active: false
        }, {
            title: '5-初级',
            passed: true,
            active: false
        }, {
            title: '6-初级',
            passed: false,
            active: false
        }
        ]
    },
    tripCourse = {
        name: '旅游英语',
        list: [{
            title: '旅游英语',
            passed: false,
            active: false
        }]
    },
    businessCourse = {
        name: '商务英语',
        list: [{
            title: '通信',
            passed: false,
            active: false
        }, {
            title: '管理',
            passed: false,
            active: false
        }, {
            title: '会议',
            passed: false,
            active: false
        }, {
            title: '谈判',
            passed: false,
            active: false
        }, {
            title: '演讲',
            passed: false,
            active: false
        }, {
            title: '社交技巧',
            passed: false,
            active: false
        }, {
            title: '接打电话',
            passed: false,
            active: false
        }, {
            title: '项目管理',
            passed: false,
            active: false
        }]
    },
    industryCourse = {
        name: '行业英语',
        grade: 2,
        list: [[{
            title: '汽车',
            passed: false,
            active: false
        }, {
            title: '航空 I',
            passed: false,
            active: false
        }, {
            title: '航空 II',
            passed: false,
            active: false
        }, {
            title: '航空 III',
            passed: false,
            active: false
        }, {
            title: '银行和金融',
            passed: false,
            active: false
        }, {
            title: '建筑',
            passed: false,
            active: false
        }, {
            title: '酒店业',
            passed: false,
            active: false
        }, {
            title: '保险',
            passed: false,
            active: false
        }], [{
            title: '信息技术行业',
            passed: false,
            active: false
        }, {
            title: '法律',
            passed: false,
            active: false
        }, {
            title: '物流',
            passed: false,
            active: false
        }, {
            title: '医疗行业',
            passed: false,
            active: false
        }, {
            title: '军事 I',
            passed: false,
            active: false
        }, {
            title: '军事 II',
            passed: false,
            active: false
        }, {
            title: '军事 III',
            passed: false,
            active: false
        }, {
            title: '办公室',
            passed: false,
            active: false
        }], [{
            title: '石油和天然气行业',
            passed: false,
            active: false
        }, {
            title: '医药',
            passed: false,
            active: false
        }, {
            title: '警方与移民 I',
            passed: false,
            active: false
        }, {
            title: '警方与移民 II',
            passed: false,
            active: false
        }, {
            title: '警方与移民 III',
            passed: false,
            active: false
        }, {
            title: '研究',
            passed: false,
            active: false
        }, {
            title: '科学',
            passed: false,
            active: false
        }, {
            title: '社会与休闲',
            passed: false,
            active: false
        }], [{
            title: '钢铁与采矿 I',
            passed: false,
            active: false
        }, {
            title: '钢铁与采矿 II',
            passed: false,
            active: false
        }, {
            title: '钢铁与采矿 III',
            passed: false,
            active: false
        }, {
            title: '电信',
            passed: false,
            active: false
        }, {
            title: '旅游业',
            passed: false,
            active: false
        }]
        ]
    }
</script>

<template>
    <div class="ets-wrap">
        <!-- 选择级别 -->
        <div class="ets-change-level-container">
            <div class="ets-chl-nav-container">
                <div class="ets-chl-nav">
                    <span class="ets-chl-current-level" @click="changeLevel">
                        <span class="ets-chl-current-level-course">普通英语:</span>
                        <span class="ets-chl-current-level-name">1-入门级</span>
                        <span class="ets-chl-btn"></span>
                    </span>
                </div>
            </div>
            
            <!-- 选项 -->
            <Transition name="options">
                <div class="ets-chl-options-container ets-chl-options-container-hidden" v-show="showOptions">
                    <div class="ets-chl-options">
                        <!-- 普通英语 -->
                        <OptionsCourseContainer :course-name="orderCourse.name" :course-list="orderCourse.list">
                            <li class="ets-chl-options-notify-container">
                                <span class="ets-chl-options-notify">更多阶段</span>
                            </li>
                        </OptionsCourseContainer>

                        <!-- 旅游英语 -->
                        <OptionsCourseContainer :course-name="tripCourse.name" :course-list="tripCourse.list" />

                        <!-- 商务英语 -->
                        <OptionsCourseContainer :course-name="businessCourse.name" :course-list="businessCourse.list" />

                        <!-- 行业英语 -->
                        <OptionsCourseContainer :course-name="industryCourse.name" :course-list="industryCourse.list" :grade="2" />
                    </div>
                </div>
            </Transition>
        </div>

        <!-- 其它 -->
        <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
    </div>
    
    <RouterView />
</template>

<style scoped>
.ets-wrap {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 13px;
    color: #222;
    line-height: 1.2;
    min-height: 100vh;
    background: #cdd2d8 url("./assets/images/bgPage.png") repeat-x;
    z-index: 0;
}

.ets-chl-nav-container {
    width: 100%;
    position: relative;
    height: 50px;
    padding-top: 15px;
    z-index: 1;
}

.ets-chl-nav {
    color: #505a68;
    width: 770px;
    margin: 0 auto;
}

.ets-chl-current-level {
    height: 15px;
    float: left;
    cursor: pointer;
}

.ets-chl-current-level-course {
    font-weight: 700;
    padding-right: 2px;
    font-size: 14px;
    float: left;
    white-space: nowrap;
}

.ets-chl-current-level-name {
    font-size: 14px;
    padding-right: 10px;
    float: left;
    white-space: nowrap;
}

.ets-chl-btn {
    background: url("./assets/images/ets-ui-main.png") no-repeat;
    float: left;
    width: 7px;
    height: 5px;
    position: relative;
    top: 6px;
}

.ets-chl-options-container {
    width: 100%;
    height: auto;
    max-height: 650px;
    background: #b4bbc6 url("./assets/images/ets-ui-change-level-container-pattern.png");
    position: relative;
    top: -50px;
}

.ets-chl-options {
    padding: 32px 0 25px;
    width: 907px;
    margin: 0 auto;
    position: relative;
    overflow: hidden;                
}

.ets-none {
    display: none;
}

.ets-chl-alert {
    background: #3b4148 url("./assets/images/ets-chl-alert-bg.png") top left repeat-x;
    width: 814px;
    height: auto;
    position: fixed;
    z-index: 300;
    padding: 30px 0;
    white-space: normal;
    color: #FFF;
}

.ets-chl-options-notify-container {
    display: block;
    padding-left: 18px;
    border-bottom: 1px transparent solid;
}

.ets-chl-options-notify {
    display: block;
    padding: 7px 0 7px 2px;
}

.ets-chl-options-notify:hover {
    background-color: #454B53;
}

.options-enter-from,
.options-leave-to {
    opacity: 0;
    max-height: 0;
    overflow: hidden;
}

.options-enter-active,
.options-leave-active {
    transition: all 0.5s ease-in-out;
}

.options-enter-to {
    overflow: auto;
}


nav {
    width: 100%;
    font-size: 12px;
    text-align: center;
}

nav a.router-link-exact-active {
    color: var(--color-text);
}

nav a.router-link-exact-active:hover {
    background-color: transparent;
}

nav a {
    display: inline-block;
    padding: 0 1rem;
    border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
    border: 0;
}

</style>
