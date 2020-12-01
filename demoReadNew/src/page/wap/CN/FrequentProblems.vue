<template>
    <f7-page class="frequentProblemsPages">
        <navbar title="常见问题" back="/Member/MyCenter"></navbar>
        <div class="section">
            <ul class="faq">
                <li v-for="(fItem ,find) in faqList" :key="find">
                    <div class="faqTitle">{{fItem.tit}}</div>
                    <div class="faqExplain">{{fItem.exp}}</div>
                    <div class="faqExplain" v-if="fItem.expsub">{{fItem.expsub}}</div>
                </li>
            </ul>

        </div>
        <!-- 全屏loader -->
        <!-- <loaderPage :bgBlack="true"></loaderPage> -->
    </f7-page>
</template>

<script>
import {
    prefix,
    buildImg,
    cookie,
    numbersAndLetters,
    clearUser
} from "@/config/env";
import navbar from "@/components/wap/common/nosearchnavbar";
import { mapGetters, mapActions } from "vuex";
import TYPES from "@/store/mutation-types";
import wsCache from "web-storage-cache";
import jsCookie from "js-cookie";

let cache = new wsCache();
export default {
    data() {
        const faqList = [
            {
                tit: "天宇头条是什么？",
                exp: "天宇头条是一款移动端资讯阅读软件。用户可以通过阅读、签到、邀请好友、做任务等方式赚取积分兑换或商品。",
                expsub: ""
            },
            {
                tit: "天宇头条为什么会给用户奖励？",
                exp: "为题引领全民阅读，帮助大家养成良好的阅读习惯，在阅读文章的过程中，天宇头条将给予一定的奖励！让您在阅读过程中不仅增长见识，而且还能有所收益！",
                expsub: ""
            },
            {
                tit: "邀请好友有什么好处？",
                exp: "邀请好友能让你的收益迅速增加。现在每邀请一位有效好友可获得至少5元奖励，你的好友越多，收益越大。",
                expsub: ""
            },
            {
                tit: "分享出去的二维码打不开怎么办？",
                exp: '方法1：告诉朋友到手机应用商店，搜索"天宇头条"下载安装，注册登陆后到右下角"我的"界面找到"输入邀请码"一栏，填写您的邀请码完成绑定 ',
                expsub: '方法2：重新分享一次二维码给朋友，最新的可正常打开 （如果多次尝试失败，可点击"我的"找到"联系客服"获得帮助）'
            },
            {
                tit: '邀请好友的提成收益有上限吗？',
                exp: '没有上限，邀请好友越多收益越多。',
                expsub: ''
            },

        ]
        return {
            faqList,
            logoIcon: buildImg(require("@/assets/wap/images/logo.png")),
            loginIcon01: buildImg(
                require("@/assets/wap/images/Login/loginIcon01.png")
            ),
            loginIcon02: buildImg(
                require("@/assets/wap/images/Login/loginIcon02.png")
            )
        };
    },
    created() { },
    computed: {
        ...mapGetters(["UserInfo"])
    },
    components: { navbar },
    methods: {
        jumpLink(url) {
            window.jumpLink(url, "_router");
        }
    }
};
</script>



<style lang="scss" scoped>
@import "../../../style/mixin";
.frequentProblemsPages {
    // background: #f5f5f5;
    .section {
        padding: 0.3rem 0.6rem 4rem;
        width: 100%;
        .faq {
            > li {
                .faqTitle {
                    font-size: 0.75rem;
                    font-weight: bold;
                    color: #2b2b2b;
                    padding: 0.6rem 0 0.2rem;
                }
                .faqExplain {
                    color: #666;
                }
            }
        }
    }
}
// 搜索栏

// .searchBox {
//   background: #ffffff;
//   display: flex;
//   width: 100%;
//   align-items: center;
//   justify-content: center;
//   border-bottom: 1px solid #fac307;

//   li.leftSide {
//     flex: 1;
//     .icon-back-arrow {
//       color: #ffc001;
//       font-size: 1.35rem;
//     }
//   }
//   li.rightSide {
//     flex: 20;
//     position: relative;
//     color: #030303;
//     text-align: center;
//     text-indent: -15%;
//     font-size: 0.7rem;
//     font-weight: bold;
//   }
// }
</style>


