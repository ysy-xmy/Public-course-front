<template>
    <div class="w-screen flex px-6 justify-center content-start items-start flex-wrap">
        <div class="course-box m-4   w-96 " v-for="(item, index) in courselist">
            <div class="course-card  card w-96 bg-base-100 shadow-xl">
                <!-- <figure><img src="https://daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.jpg" alt="Shoes" />
            </figure> -->
                <div class="card-body">
                    <h2 class="card-title">
                        {{ item.kc }}
                        <div class="badge badge-secondary  w-16 whitespace-nowrap">{{ item.kcsx }}</div>
                        <div class="badge  badge-accent w-20 whitespace-nowrap">莞城</div>

                    </h2>

                    <p>If a dog chews shoes whose shoes does he choose?</p>
                    <div class="card-actions justify-between">
                        <div class="flex flex-nowrap">

                            <div class=" badge-outline">黄为</div>

                        </div>
                        <div class="flex flex-wrap justify-end ">
                            <div class=" badge-outline ">学分：{{ item.xf }} &nbsp;</div>

                            <br>
                            <div class=" badge-outline">总学时：{{ item.zxs }}</div>
                        </div>

                    </div>
                    <div class="progress-box flex flex-nowrap items-center content-center">
                        <progress class="progress progress-accent w-11/12" value="70" max="100"></progress>
                        <span class="ml-2 text-sm">1/100</span>
                    </div>


                </div>
            </div>

        </div>
    </div>



</template>

<script setup lang="ts">
import { ref } from 'vue';

// const course = ref({
//     "kc": "[1310602](面授公选)合唱",
//     "xf": "2.0",
//     "zxs": "32",
//     "lb": "公共课/任选课",
//     "kcsx": "通识(审美)/理论课",
//     "skbjdm": "",
//     "xkfs": "",
//     "rkjs": "",
//     "xk_points": "",
//     "is_buy_book": "",
//     "is_cx": "",
//     "xk_status": "",
//     "operation": "选择",
//     "kcdm": "1310602",
//     "kclb1": "03",
//     "kclb2": "01",
//     "khfs": "02",
//     "kclb3": "20",
//     "is_yxtj": "",
//     "skbzdm": ""
// });
// teacher, 校区，已选人数，可选人数，上课时间，上课地点

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
}

// 确保course的类型与Course接口匹配
const course = ref<Course>({
    // ... (同样的对象)
});

const courselist = [
    {
        "kc": "[0310468](混合公选)意大利文化",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "0310468-002",
        "xkfs": "学生网上选",
        "rkjs": "[2021011]陈晓涌",
        "xk_points": "0",
        "is_buy_book": "0",
        "is_cx": "0",
        "xk_status": "选中",
        "operation": "查看 | 退选",
        "kcdm": "0310468",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "1",
        "skbzdm": ""
    },
    {
        "kc": "[0811023](混合公选)解读中国经济发展的密码",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(协作)/理论课",
        "skbjdm": "0811023-001",
        "xkfs": "学生网上选",
        "rkjs": "[1997003]黄琼",
        "xk_points": "0",
        "is_buy_book": "0",
        "is_cx": "0",
        "xk_status": "选中",
        "operation": "查看 | 退选",
        "kcdm": "0811023",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "21",
        "is_yxtj": "1",
        "skbzdm": ""
    },
    {
        "kc": "[0210457](面授公选)发光与显示",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(认知)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "20202364",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "22",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0210768](混合公选)数学的思维方式与创新",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(认知)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0210768",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "22",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0210793](混合公选)精读《未来简史》",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(高阶)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0210793",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "24",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0310465](混合公选)科幻中的物理学",
        "xf": "1.5",
        "zxs": "24",
        "lb": "公共课/任选课",
        "kcsx": "通识(高阶)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0310465",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "24",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0310467](混合公选)拉美文化",
        "xf": "1.5",
        "zxs": "24",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0310467",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0410258](面授公选)数学建模",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(应用)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "382205",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "23",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0410495](面授公选)功夫与防身技术",
        "xf": "2.0",
        "zxs": "33",
        "lb": "公共课/任选课",
        "kcsx": "通识(应用)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0410495",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "23",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0710042](混合公选)法律与社会",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(道德)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0710042",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "19",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0710043](混合公选)大学生恋爱与性健康",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(道德)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0710043",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "19",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0810958](混合公选)外经贸英语函电",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0810958",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811022](混合公选)推开经济学之门",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(协作)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811022",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "21",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811024](混合公选)经济学原理（上）：中国故事",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(协作)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811024",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "21",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811030](混合公选)经济基础与应用",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(应用)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811030",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "23",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811032](混合公选)有效沟通技巧",
        "xf": "1.0",
        "zxs": "16",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811032",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811034](混合公选)电影与幸福感",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(认知)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811034",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "22",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[0811035](混合公选)东方电影",
        "xf": "1.0",
        "zxs": "16",
        "lb": "公共课/任选课",
        "kcsx": "通识(认知)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "0811035",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "22",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1010871](混合公选)情绪管理",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1010871",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1010872](混合公选)欧洲文明概论",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1010872",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1010873](混合公选)东南亚文化",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(沟通)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1010873",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "25",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1010878](面授公选)摄影",
        "xf": "1.5",
        "zxs": "24",
        "lb": "公共课/任选课",
        "kcsx": "通识(审美)",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "203000614",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "20",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1110529](面授公选)公共管理",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(认知)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1110529",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "22",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1110530](面授公选)公益慈善",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(道德)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1110530",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "19",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1110531](面授公选)社会保障学",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(应用)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1110531",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "23",
        "is_yxtj": "",
        "skbzdm": ""
    },
    {
        "kc": "[1310602](面授公选)合唱",
        "xf": "2.0",
        "zxs": "32",
        "lb": "公共课/任选课",
        "kcsx": "通识(审美)/理论课",
        "skbjdm": "",
        "xkfs": "",
        "rkjs": "",
        "xk_points": "",
        "is_buy_book": "",
        "is_cx": "",
        "xk_status": "",
        "operation": "选择",
        "kcdm": "1310602",
        "kclb1": "03",
        "kclb2": "01",
        "khfs": "02",
        "kclb3": "20",
        "is_yxtj": "",
        "skbzdm": ""
    }
]

for (let i = 0; i < courselist.length; i++) {
    courselist[i].kcsx = courselist[i].kcsx.replaceAll('通识', '').replaceAll('/理论课', '').replaceAll('(', "").replaceAll(')', '')
}



</script>


<style></style>
