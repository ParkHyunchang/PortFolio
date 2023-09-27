<script setup>
    import { pictureText } from "@/constants/index";
</script>

<template>
    <section id="picture">
        <div class="picture__inner">
            <div class="picture__title">
                picture <em>사진</em>
            </div>
            <div class="picture__wrap">
                <div class="picture__item" v-for="(picture, key) in pictureText" :key="key">
                    <span class="num">{{ picture.num }}.</span>
                    <img :src="picture.img" :alt="picture.name" />
                    <h3 class="title">{{ picture.title }}</h3>
                    <!-- <p class="desc">{{ picture.desc }}</p> -->
                    <!-- <a :href="picture.view" target="_blank" class="site">사이트 보기</a> -->
                </div>
            </div>
        </div>
    </section>
</template> 

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
    mounted: function(){
        this.scrollAnimation();
    },
    methods: {
        scrollAnimation(){
            const horSection = gsap.utils.toArray(".picture__item");

            gsap.to(horSection, {
                xPercent: -120 * (horSection.length - 1),
                ease: "none",
                scrollTrigger: {
                    trigger: "#picture",
                    start: "top 56px",
                    end: "+=3000",
                    pin: true,
                    scrub: 1,
                    markers: false,
                    invalidateOnRefresh: true,
                    anticipatePin: 1,
                },
            });
        }
    }
}
</script>

<style lang="scss">
#picture {
    width: 100%;
    margin-top: 30vh;
    // overflow: hidden;
}
.picture__inner {
    padding: 16px;

    .picture__title {
        width: 100%;
        height: 5vw;
        font-size: 4vw;
        font-weight: 900;
        line-height: 1.6;
        font-family: var(--mainKor-font);
        text-transform: uppercase;
        color: var(--black100);
        border-bottom: 0.4vw solid var(--black100);
        margin-bottom: 16px;
        text-indent: -0.26vw;

        em {
            font-size: 1.25rem;
            font-weight: 400;
            line-height: 2;
        }
    }
    .picture__wrap {
        display: flex;
        flex-wrap: wrap;
        width: 7000px;

        .picture__item {
            width: 500px;
            height: 100vh;
            background-color: var(--subBg100);
            padding: 2.5rem;
            margin-right: 20px;

            &.p1 {
                background-color: var(--subBg100);
            }
            &.p2 {
                background-color: var(--subBg200);
            }
            &.p3 {
                background-color: var(--subBg300);
            }
            &.p4 {
                background-color: var(--subBg400);
            }
            &.p5 {
                background-color: var(--subBg500);
            }
            &.p6 {
                background-color: var(--subBg100);
            }
            &.p7 {
                background-color: var(--subBg200);
            }
            &.p8 {
                background-color: var(--subBg300);
            }
            &.p9 {
                background-color: var(--subBg400);
            }
            &.p10 {
                background-color: var(--subBg500);
            }
            .num {
                font-size: 2rem;
                font-family: var(--mainNum-font);
            }
            .img {
                display: block;
                margin-top: -20px;
                transition: margin-top 0.3s;

                img {
                    border-radius: 5px;
                    filter: saturate(0%);
                    transition: all 0.3s;
                }
                
                &:hover {
                    margin-top: 0;

                    img {
                        filter: saturate(100%);
                    }
                }
            }
            .title {
                font-size: 1.5rem;
                text-align: center;
                padding: 0.8rem 0;
                font-weight: 700;
                color: var(--black100);
                border-bottom: 2px solid var(--black100);
                margin-bottom: 1rem;
            }
            .desc {
                font-size: 1rem;
            }
            .site {
                border: 1px solid var(--black100);
                display: block;
                text-align: center;
                padding: 0.625rem 1.5rem;
                margin-top: 1.5rem;
                transition: all 0.2s;

                &:hover {
                    background-color: var(--black100);
                    color: var(--white);
                }
            }
        }
    }
}
</style>