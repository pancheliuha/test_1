<template>
    <div class="main-wrapper">
        <div class="bg-wrapper">
            <template v-for="i in 10">
                <transition
                        name="fade-out"
                        leave-active-class="opacity-in"
                >
                    <div v-show="step === i - 1" class="bg-section" :style="{background: `url(${require(`../assets/img/test-bg/test-${i - 1}-bg.jpg`)}) center no-repeat / cover`}"></div>
                </transition>
            </template>
        </div>

        <aside class="aside-section">
            <div class="test-item-wrapper">
                <img class="logo-mobile" src="../assets/img/icons/cardio-logo.png" alt="logo">
                <transition
                        name="fade-out"
                        leave-active-class="opacity-in"
                >
                    <start-component v-if="step === 0"></start-component>
                </transition>


                <transition
                        name="fade-out"
                        leave-active-class="opacity-in">
                    <test-item-range  v-if="step === 1"></test-item-range>
                </transition>

                <template v-for="testItem in testsArr">
                    <transition
                            name="fade-out"
                            leave-active-class="opacity-in">
                        <test-item
                                v-show="testItem.id === step"
                                :key="testItem.id"
                                :testNumber="testItem.number"
                                :trueBtnText="testItem.trueBtnText"
                                :falseBtnText="testItem.falseBtnText"
                                :inverseBtns="testItem.inverseBtns"
                                :testText="testItem.text"
                        >
                        </test-item>
                    </transition>
                </template>
            </div>
        </aside>
        <img class="logo" src="../assets/img/icons/cardio-logo.png" alt="logo">
    </div>
</template>

<script>
import tests from '../files/tests';
import StartComponent from './Start.vue';
import TestItemRange from './TestItemRange.vue';
import TestItem from './TestItem.vue';
import { redirectUrl } from '../config.js'

export default {
    name: 'Main',
    components: {
        StartComponent,
        TestItemRange,
        TestItem
    },
    data () {
        return {
            step: 0,
            testCount: 0,
            testsArr: tests
        }
    },
    methods: {
        goToFirstStep() {
          this.step++;
        },

        goToNextStep(stepTestCount) {
            this.testCount += stepTestCount;
            if (this.step === 9) {
                console.log('redirect');
                let searchParams = `/test-result?result=${this.testCount}`
                location.href = `${redirectUrl}${searchParams}`;
                return;
            }
            this.step++;
        }
    },
    mounted() {
        this.$root.$on('goToFirstStep', this.goToFirstStep);
        this.$root.$on('goToNextStep', this.goToNextStep);
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    @import "../assets/scss/_mixins.scss";
    /* eslint-disable */
    .main-wrapper {
        display: flex;
        width: 100%;
        height: 100%;
        position: relative;
        overflow: hidden;
        @include laptop() {
            flex-direction: column;
            overflow: auto;
            align-items: center;
        }
    }

    .logo {
        position: absolute;
        top: 40px;
        right: 65px;
        @include desktop() {
            width: 90px;
            right: 35px;
            top: 25px;
        }
        @include laptop() {
            display: none;
        }
    }

    .logo-mobile {
        display: none;
        @include laptop() {
            position: absolute;
            top: 30px;
            right: 30px;
            display: inline-block;
            width: 84px;
        }
        @include phones() {
            right: 0;
        }
    }

    .bg-wrapper {
        flex-grow: 1;
        position: relative;
        @include laptop() {
            width: 100%;
            height: 70vw;
            flex-grow: 0;
        }
    }

    .bg-section {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
    }

    .aside-section {
        width: 500px;
        padding: 0 65px 65px;
        background-color: #fff;
        @include desktop() {
            padding: 0 35px 50px;
            width: 400px;
        }
        @include laptop() {
            width: 80%
        }
        @include phones() {
            width: 100%;
            padding: 0 15px;
        }
    }

    .test-content {
        @include laptop() {
            margin-bottom: 25px;
        }
    }

</style>
