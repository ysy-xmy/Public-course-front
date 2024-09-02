<template>
    <div class="top flex w-full justify-center item content-center pt-3">
        <div class="select-box w-full grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-5 gap-2 px-4">

            <select v-model="selectedCampus" @change="changeinput" class="select select-bordered">
                <option value="" selected>校区：全部</option>
                <option value="1">松山湖</option>
                <option value="2">莞城</option>

            </select>
            <select v-model="selecttype" @change="changeinput" class="select select-bordered">
                <option value="" selected>类别：全部</option>
                <option value="沟通">沟通</option>
                <option value="高阶">高阶</option>
                <option value="认知">认知</option>
                <option value="应用">应用</option>

                <option value="道德">道德</option>

                <option value="审美">审美</option>

                <option value="协作">协作</option>
            </select>
            <select v-model="selecttime" @change="changeinput" class="select select-bordered">
                <option value="" selected>时间：全部</option>
                <option value="周 一">周一</option>
                <option value="周 二">周二</option>
                <option value="周 三">周三</option>
                <option value="周 四">周四</option>
                <option value="周 五">周五</option>
                <option value="周 六">周六</option>
                <option value="周 日">周日</option>

            </select>
            <select v-model="selectMode" @change="changeinput" class="select select-bordered">
                <option value="" selected>类型：全部</option>
                <option value="混合公选">混合公选</option>
                <option value="面授公选">面授公选</option>
            </select>

            <div class="search md:w-auto w-full ">
                <div class="group md:w-auto w-full">
                    <svg viewBox="0 0 24 24" aria-hidden="true" class="icon">
                        <g>
                            <path
                                d="M21.53 20.47l-3.66-3.66C19.195 15.24 20 13.214 20 11c0-4.97-4.03-9-9-9s-9 4.03-9 9 4.03 9 9 9c2.215 0 4.24-.804 5.808-2.13l3.66 3.66c.147.146.34.22.53.22s.385-.073.53-.22c.295-.293.295-.767.002-1.06zM3.5 11c0-4.135 3.365-7.5 7.5-7.5s7.5 3.365 7.5 7.5-3.365 7.5-7.5 7.5-7.5-3.365-7.5-7.5z">
                            </path>
                        </g>
                    </svg>
                    <input @keyup="changeinput" class="input" v-model="coursename" type="search" placeholder="Search" />
                </div>

            </div>
        </div>

    </div>
    <div class="w-full flex justify-center">
        <div class="divider h-1 w-11/12 divider-end text-[#abacac]">共找到{{ showdata.length }}个课程</div>
    </div>

    <div class="w-screen flex px-6 justify-center content-start items-start flex-wrap">

        <div class="course-box m-4   w-96 " v-for="(item, index) in showdata">
            <div class="course-card  card w-96 bg-base-100 shadow-xl">
                <!-- <figure><img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" alt="Shoes" />
            </figure> -->
                <div class="card-body">
                    <h2 class="card-title">
                        {{ item.kc }}
                        <div class="badge badge-secondary  w-16 whitespace-nowrap">{{ item.kcsx }}</div>
                        <div class="badge  badge-accent w-20 whitespace-nowrap">{{ item.xqdm == '1' ? '松山湖' : '莞城' }}
                        </div>

                    </h2>
                    <div class="w-full px-2">

                        <p>时间：<span class="font-bold underline">{{ item.sksj }}</span> </p>
                        <p>教室：{{ item.skdd }} </p>
                    </div>

                    <div class="card-actions justify-between">
                        <div class="flex flex-nowrap">

                            <div class=" badge-outline">[{{ item.kcdm }}] {{ item.rkjs }}</div>
                        </div>
                        <div class="flex flex-wrap justify-end ">
                            <div class=" badge-outline ">学分：{{ item.xf }} &nbsp;</div>

                            <br>
                            <div class=" badge-outline">总学时：{{ item.zxs }}</div>
                        </div>

                    </div>
                    <div class="progress-box flex flex-nowrap items-center content-center">
                        <progress class="progress progress-accent w-11/12" :value=item.yxrs :max=item.xkrssx></progress>
                        <span class="ml-2 text-sm">{{ item.yxrs }}/{{ item.xkrssx }}</span>
                    </div>


                </div>
            </div>

        </div>
    </div>



</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import axios from 'axios';

interface Course {
    kc: string;
    xf: string;
    zxs: string;
    lb: string;
    kcsx: string;
    skbjdm: string;
    xkfs: string;
    rkjs: string;
    xk_points: string;
    is_buy_book: string;
    is_cx: string;
    xk_status: string;
    operation: string;
    kcdm: string;
    kclb1: string;
    kclb2: string;
    khfs: string;
    kclb3: string;
    is_yxtj: string;
    skbzdm: string;
    skbjmc: string;
    skbzmc: string;
    xqmc: string;
    skfs_mc: string;
    xkrssx: string;
    xkrs: string;
    kxrs: string;
    sksj: string;
    skdd: string;
    ischk: string;
    xqdm: string;
    skfs_m: string;
    outnumber: string;
    yxrs: string;
    yxsyxkb: string;


}




const courselist = ref<Course[]>([]);
const selectedCampus: string = ref('')
const showdata: Array = ref([])
const selecttype: string = ref('')
const selectMode: string = ref('')
const coursename: string = ref('')


const changeinput = () => {
    let temp = courselist.value.filter((item) => {
        return item.kc.includes(coursename.value)
    }).filter((item) => {
        return item.kc.includes(selectMode.value)
    }).filter((item) => {
        return item.xqdm.includes(selectedCampus.value)
    }).filter((item) => {
        return item.kcsx.includes(selecttype.value)
    }).filter((item) => {
        return item.sksj.includes(selecttime.value)
    })
    showdata.value = temp
}
const selecttime: string = ref('')

onMounted(() => {


    axios.get('https://meet.ysyxmy.top:1814/api/courselist').then((res) => {
        console.log(res.data.data);
        courselist.value = res.data.data;
        for (let i = 0; i < courselist.value.length; i++) {
            courselist.value[i].kcsx = courselist.value[i].kcsx.replaceAll('通识', '').replaceAll('/理论课', '').replaceAll('(', "").replaceAll(')', '')
            courselist.value[i].yxrs = parseInt(courselist.value[i].xkrssx) - parseInt(courselist.value[i].kxrs);
            courselist.value[i].kc = courselist.value[i].kc.split(']')[1]
            courselist.value[i].rkjs = courselist.value[i].rkjs.split(']')[1]

        }
        showdata.value = courselist.value
    });
});




</script>


<style scoped>
.search {
    display: flex;
    align-items: center;
    justify-content: space-between;
    text-align: center;
    position: relative;

}

.group {
    display: flex;
    line-height: 28px;
    align-items: center;
    position: relative;
    width: 100%;
}

.input {
    width: 100%;
    height: 40px;
    line-height: 28px;
    padding: 0 1rem;
    padding-left: 2.5rem;
    border: 2px solid transparent;
    border-radius: 8px;
    outline: none;
    background-color: #f3f3f4;
    color: #0d0c22;
    transition: 0.3s ease;
}

.input::placeholder {
    color: #9e9ea7;
}

.input:focus,
input:hover {
    outline: none;
    border-color: rgba(0, 48, 73, 0.4);
    background-color: #fff;
    box-shadow: 0 0 0 4px rgb(0 48 73 / 10%);
}

.icon {
    position: absolute;
    left: 1rem;
    fill: #9e9ea7;
    width: 1rem;
    height: 1rem;
}
</style>
