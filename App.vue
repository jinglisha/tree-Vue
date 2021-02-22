<template>
    <div class="app">
        <!-- 使用子组件 -->
        <base-tree :data="data" />
    </div>
</template>

<script>
// 引入tree组件
import BaseTree from "./Tree";
export default {
    components: {
        // 子组件
        BaseTree,
    },
    data() {
        return {
            // 传入的数据
            data: [
                {
                    label: "一级 1",
                    children: [
                        {
                            label: "二级 1-1",
                            children: [
                                {
                                    label: "三级 1-1-1",
                                },
                            ],
                        },
                    ],
                },
                {
                    label: "一级 2",
                    children: [
                        {
                            label: "二级 2-1",
                            children: [
                                {
                                    label: "三级 2-1-1",
                                },
                            ],
                        },
                        {
                            label: "二级 2-2",
                            children: [
                                {
                                    label: "三级 2-2-1",
                                },
                            ],
                        },
                    ],
                },
                {
                    label: "一级 3",
                    children: [
                        {
                            label: "二级 3-1",
                            children: [
                                {
                                    label: "三级 3-1-1",
                                },
                            ],
                        },
                        {
                            label: "二级 3-2",
                            children: [
                                {
                                    label: "三级 3-2-1",
                                },
                            ],
                        },
                    ],
                },
            ],
        };
    },
};
</script>

<style scoped>
</style>