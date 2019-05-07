<!--  Create by YangChen on 2019/5/6 15:44  -->
<template>
    <div>

    </div>
</template>

<script>
    export default {
        name: 'curryTemp',
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


    let currying = function (fn) {
        let _arg = [];
        return function cb() {
            if (arguments.length === 0){
                return fn.apply(this,_arg);
            }
            Array.prototype.push.apply(_arg,[].slice.call(arguments));
            return cb;
        }
    };
    let result = 0;
    function add() {
        console.log('this',this);
        for(let i = 0 ; i<arguments.length;i++){
            result += arguments[i];
        }
        console.log('result',result)
    }
    let s = currying(add)
    s(1)(2)(3)(4)();
</script>

<style scoped>

</style>
