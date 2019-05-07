<!--  Create by YangChen on 2019/5/6 15:42  -->
<template>
    <div>

    </div>
</template>

<script>
    export default {
        name: 'ObjectExtends',
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


    /*定义一个人类*/
    function Person(name,age,test,test2){

        this.name=name;
        this.age=age;
    }
    /*定义一个学生类*/
    function Student(name,age,grade){
        Person.apply(this,arguments);
        this.grade=grade;
    }
    //创建一个学生类
    let student=new Student("zhangsan",21,"一年级");
    //测试
    // console.log("name:"+student.name+"\n"+"age:"+student.age+"\n"+"grade:"+student.grade);
    //大家可以看到测试结果name:zhangsan age:21  grade:一年级
    //学生类里面我没有给name和age属性赋值啊,为什么又存在这两个属性的值呢,这个就是apply的神奇之处.


    let array1 = new Array();
    array1.push(...['111','222','333','444']);
    Array.prototype.push.apply(array1,['555','666','777',]);
    console.info(array1);

</script>

<style scoped>

</style>
