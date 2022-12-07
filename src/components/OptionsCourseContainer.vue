<script setup>
import { defineProps } from 'vue'
import CourseLevelContainer from './CourseLevelContainer.vue'

defineProps({
    courseName: {
        type: String,
        required: true
    },

    // 层级关系：行业英语为2，其余为1
    grade: {
        type: Number,
        default: 1
    },

    courseList: {
        type: Array,
        required: true
    }
});
</script>

<template>
    <div class="ets-chl-options-course-container">
        <ul class="ets-chl-options-course">
            <li class="ets-chl-options-course-name-container">
                <span class="ets-chl-options-course-name ellipsis">{{ courseName }}</span>
            </li>
            
            <li class="ets-chl-course-level-group ets-chl-course-level-first-group" v-if="(grade === 1)">
                <ul>
                    <CourseLevelContainer
                        v-for="(item, index) in courseList"
                        :key="index"
                        v-bind="item"
                    />

                    <slot></slot>
                </ul>
            </li>

            <template v-else>
                <li :class="['ets-chl-course-level-group', {'ets-chl-course-level-first-group': m === 0}]" v-for="(list, m) in courseList" :key="m">
                    <ul>
                        <CourseLevelContainer
                            v-for="(item, n) in list"
                            :key="n"
                            v-bind="item"
                        />
                    </ul>
                </li>
            </template>
        </ul>
    </div>
</template>

<style scoped>
.ets-chl-options-course-container {
    padding: 23px 9px 0;
    height: 291px;
    width: auto;
    float: left;
}

.ets-chl-options-course {
    display: inline-block;
    min-height: 37px;
    min-width: 185px;
    height: 268px;
    padding: 6px 22px 17px 0;
    background: #aab2bc url("../assets/images/ets-ui-change-level-options-content.png");
    border-radius: 5px;
    border: 1px solid #8D94A0;
    box-shadow: inset 0 0 3px #999;
    cursor: pointer;
    color: #FFF;
}

.ets-chl-options-course:hover {
    background: #949ba4 url("../assets/images/ets-ui-change-level-options-content-hover.png");
    border: 1px solid #676D75;
    box-shadow: inset 0 0 10px #888;
}

.ets-chl-options-course-name {
    display: inline-block;
    padding: 0 0 6px 2px;
    font-weight: 700;
    font-size: 14px;
    border-bottom: 1px solid #CCC;
    width: 163px;
}

.ets-chl-options-course-name-container {
    width: 183px;
    padding-left: 18px;
}

.ets-chl-course-level-group {
    float: left;
    margin-left: 41px;
    width: 183px;
    font-size: 12px;
}

.ets-chl-course-level-first-group {
    margin-left: 0;
}
</style>