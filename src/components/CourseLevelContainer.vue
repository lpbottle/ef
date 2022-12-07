<script setup>
import { defineProps } from 'vue'
defineProps({
    title: {
        type: String,
        required: true
    },

    // 该级别是否通过
    passed: {
        type: Boolean,
        default: false
    },

    // 当前选中了哪个级别
    active: {
        type: Boolean,
        default: false
    }
});
</script>

<template>
    <li :class="['ets-chl-course-level-container', { 'ets-active': active }]" >
        <span class="ets-chl-course-level">
            <span class="ets-chl-course-level-name ellipsis">
                {{ title }}
            </span>
            <span :class="[{'ets-passed': passed}, 'ets-chl-course-level-status']"></span>
        </span>
    </li>
</template>

<style scoped>
.ets-chl-course-level-container {
    display: block;
    padding-left: 18px;
    border-bottom: 1px transparent solid;
    overflow: hidden;
}

.ets-chl-course-level-container.ets-active {
    height: 27px;
    background: #454b53 url("./../assets/images/ets-ui-change-level.png") -145px 7px no-repeat;
    border-bottom-color: #B7BDC5;
}

.ets-chl-course-level {
    position: relative;
    display: block;
    padding: 7px 0 7px 2px;
}

.ets-chl-course-level:hover {
    background-color: #454B53;
}

.ets-chl-course-level-name {
    display: block;
    margin-right: 16px;
}

.ets-chl-course-level-status {
    position: absolute;
    right: 8px;
    top: 50%;
    width: 8px;
    height: 8px;
    margin-top: -4px;
}

.ets-chl-course-level-status.ets-passed {
    background: url("../assets/images/ets-ui-change-level.png") -123px 0 no-repeat;
}
</style>