<template>
    <div :class="`bg-[url(${the.images[0].url})]`" class="min-h-[60dvh] bg-center bg-cover flex" un-cloak>
        <div class="flex-auto bg-black/50 flex items-center">
            <div class="container mx-auto text-white flex flex-col items-center text-center gap-4">
                <div class="hvr-icon-wobble-vertical my-2">
                    <Icon :icon="the.icon" class="size-24 hvr-icon"></Icon>
                </div>
                <h1>{{ $t(`title["${the.id}"]`) }}</h1>
                <p>{{ $t(`description["${the.id}"]`) }}</p>
            </div>
        </div>
    </div>
    <div class="container mx-auto not-prose my-24 px-4 overflow-hidden">
        <UseElementVisibility v-slot="{ isVisible }"
            v-for="({ images, to, title, description, icon }, i) in the.$children" :key="id" class="not-prose">
            <div class="my-4 flex flex-col items-start gap-4 sm:flex-row animate__animated animate__faster"
                :class="{ animate__fadeInRight: isVisible, invisible: !isVisible }">
                <div @mouseover="slide[i] = true" @mouseleave="slide[i] = false" :class="`bg-[url(${images[0].url})]`"
                    class="flex w-full h-48 sm:w-48 sm:h-24 bg-center bg-cover overflow-hidden rounded">
                    <transition enter-active-class="animate__animated animate__slideInUp animate__faster"
                        leave-active-class="animate__animated animate__slideOutUp  animate__faster">
                        <router-link v-if="slide[i]" class="bg-white/85 flex-auto flex justify-center items-center"
                            :to="to">
                            <el-button size="large" circle="" tag="router-link" :to="to">
                                <icon :icon="icon"></icon>
                            </el-button>
                        </router-link>
                    </transition>
                </div>
                <router-link :to="to" class="!flex w-full min-w-0 gap-4 text-base hvr-icon-wobble-vertical group">
                    <icon :icon="icon" class="size-10 hvr-icon group-hover:text-sky-800"></icon>
                    <div class="flex flex-col items-start justify-center w-full min-w-0 gap-0 text-base">
                        <el-text size="large" tag="b" class="mb-4 w-full group-hover:text-sky-800">
                            {{ title }}
                        </el-text>
                        <el-text class="w-full">{{ description }}</el-text>
                    </div>
                </router-link>
            </div>
        </UseElementVisibility>
    </div>
</template>

<script setup lang="js">
import { inject, reactive } from "vue";
import { useI18n } from "vue-i18n";
import { UseElementVisibility } from "@vueuse/components";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    slide = reactive([]),
    { t } = useI18n({
        messages: {
            en: {
            },
            ru: {
            }
        }
    });

__unocss_runtime.extract("bg-white/85");

</script>