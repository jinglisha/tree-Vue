//  模版
<template>
    <ul class="tree">
        <li v-for="(node,index) in data" :key="node[defaultProps['label']]" class="tree-node">
            <i
                v-if="node[defaultProps['children']]"
                class="iconfont icon-down"
                :class="{
                'icon-down':showChildren[index],
                'icon-right':!showChildren[index],

            }"
            ></i>
            <span class="node-label" @click="handleClick(index)">{{node[defaultProps['label']]}}</span>

            <!-- 递归组件 -->
            <keep-alive>
                <base-tree v-if="showChildren[index] && node[defaultProps['children']]" :data="node[defaultProps['children']]" />
            </keep-alive>
        </li>
    </ul>
</template>
<script>
export default {
    name: "base-tree",
    // 注册特性
    props: {
        // 要渲染的数据
        data: {
            // 类型
            type: Array,
            // 必需
            required: true,
        },
        defaultProps: {
            type: Object,
            // 返回的值
            default: () => ({
                label: "label",
                children: "children",
            }),
        },
    },
    data() {
        return {
            showChildren: [],
        };
    },
    methods: {
        handleClick(index) {
            const flag = !this.showChildren[index];
            this.$set(this.showChildren, index, flag);
        },
    },
    mounted() {
        //console.log(this.data);
    },
};
</script>
<style scoped>
@import "./assets/font.css";
li {
    list-style: none;
}
.tree-node {
    cursor: pointer;
}
.tree-node .iconfont {
    color: #c0c4cc;
    font-size: 12px;
    margin-right: 5px;
    vertical-align: middle;
}
.tree-node .node-label {
    font-size: 14px;
    color: #606266;
    vertical-align: middle;
}
</style>