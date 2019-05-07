<!--  Create by YangChen on 2019/5/6 15:46  -->
<template>
    <div>

    </div>
</template>

<script>
    export default {
        name: 'vueStudy1',
        data() {
            return {}
        },
        computed: {},
        methods: {},
        created() {
        },
        mounted() {
        },
        watch: {}
    }




    function cb (val) {
        /* 渲染视图 */
        console.log("视图更新啦～");
    }

    function defineReactive (obj, key, val) {
        Object.defineProperty(obj, key, {
            enumerable: true,       /* 属性可枚举 */
            configurable: true,     /* 属性可被修改或删除 */
            get: function reactiveGetter () {
                return val;         /* 实际上会依赖收集，下一小节会讲 */
            },
            set: function reactiveSetter (newVal) {
                if (newVal === val) return;
                cb(newVal);
            }
        });
    }

    function observer (value) {
        if (!value || (typeof value !== 'object')) {
            return;
        }
        Object.keys(value).forEach((key) => {
            defineReactive(value, key, value[key]);
        });
    }

    class Vue {
        /* Vue构造类 */
        constructor(options) {
            this._data = options.data;
            observer(this._data);
        }
    }

    let o = new Vue({
        data: {
            test: "I am test."
        }
    });
    console.log(o)
    o._data.test = "hello,world.";  /* 视图更新啦～ */

</script>

<style scoped>

</style>
