<template>
    <div class="sticky top-0 z-50 pa-4 border-b bg-neutral-50 border-slate-200" ref="pageHeader">
        <el-page-header icon="" @back="lang">
            <!--template #breadcrumb>
                <el-breadcrumb separator="/">
                    <el-breadcrumb-item v-for="item in breadcrumbs" :to="item.to">
                        {{ item.name }}
                    </el-breadcrumb-item>
                </el-breadcrumb>
            </template-->
            <template #content>
<div class="flex items-center">
    <RouterLink to="/" class="text-3xl">🏠</RouterLink>
    <el-divider direction="vertical"></el-divider>
    <div>{{ $t(`title['${pages[$route.name].id}']`) }}</div>
</div>
            </template>
            <template #title>
                <icon :icon="t(0)" class="size-8"></icon>
            </template>
            <template #extra>
                <el-button circle @click="drawer = true" size="large">
                    <icon icon="fa-solid:bars" class="size-5"></icon>
                </el-button>
            </template>
        </el-page-header>
    </div>
    <div class="flex-auto" un-cloak>
        <RouterView></RouterView>
    </div>
    <div class="bg-black/10 border-t-2 border-orange-500" un-cloak>
        <div class="container mx-auto my-4 px-2 sm:px-none">
            <div class="grid grid-cols-1 md:grid-cols-3">
                <div class="border-l border-gray-400 pl-2 py-4">
                    <Icon icon="fa-solid:info-circle" class="size-5 text-gray-600"></Icon>
                    <div class="mt-4">
                        <el-text tag="div">{{ t(1) }}</el-text>
                        <div><el-button class="!pl-0 !border-l-0" type="danger" link tag="router-link"
                                to="/documents/agreement/">{{ t(2) }}</el-button>
                        </div>
                        <div><el-button class="!pl-0 !border-l-0" type="danger" link tag="router-link"
                                to="/documents/consent/">{{ t(3) }}</el-button></div>
                    </div>
                </div>
                <div class="border-l border-gray-400 pl-2 py-4">
                    <Icon icon="fa-solid:building" class="size-5 text-gray-600"></Icon>
                    <div class="mt-4">
                        <el-text tag="div">{{ t(4) }}</el-text>
                        <el-text tag="div">{{ t(5) }}</el-text>
                        <div><el-button class="!pl-0 !border-l-0" type="danger" link tag="router-link"
                                to="/contacts/">{{ t(6) }}</el-button>
                        </div>
                    </div>
                </div>
                <div class="border-l border-gray-400 pl-2 py-4">
                    <Icon icon="fa-solid:address-card" class="size-5 text-gray-600"></Icon>
                    <div class="mt-4">
                        <div><el-link underline="never" href="tel:+79151797755">+7 (915) 179-77-55</el-link></div>
                        <div><el-link underline="never" href="mailto:info@savamed.ru">info@savamed.ru</el-link></div>
                        <div>
                            <el-link underline="never"
                                href="https://wa.me/79151797755?text=Здравствуйте!%20Нужна%20помощь" type="danger">
                                <Icon icon="fa-brands:whatsapp" class="size-7"></Icon>
                            </el-link>
                            <el-link underline="never" href="https://t.me/+79151797755" type="danger">
                                <Icon icon="fa-brands:telegram" class="size-7"></Icon>
                            </el-link>
                        </div>
                    </div>
                </div>
            </div>
            <div class="my-4"><el-text size="small">{{ t(7) }}</el-text></div>
            <div class="mx-auto my-4 w-fit"><el-link underline="never" href="https://vuebro.ru" target="_blank">{{ t(8)
                    }}</el-link></div>
        </div>
    </div>
    <div id="drawer" un-cloak>
        <el-drawer v-model="drawer" class="w-full sm:w-96" size="">
            <!--template #header>
                <router-link class="w-full" to="/"><icon :icon="the.icon" class="mr-4 size-8 inline-block"></icon>{{ $t(`title['${the.id}']`) }}</router-link>
            </template-->
            <el-menu :router="true">
                <template v-for="{ $children, icon, id } in the.$children">
                    <el-sub-menu :index="id" v-if="$children.length">
                        <template #title>
                            <icon :icon="icon" class="mr-4 size-8"></icon><span class="truncate">{{ $t(`title["${id}"]`)
                                }}</span>
                        </template>
                        <el-menu-item v-for="child in $children" :route="{ name: child.id }" :index="child.id">
                            <icon :icon="child.icon" class="mr-4 size-8"></icon><span class="truncate">{{
                                $t(`title["${child.id}"]`)
                                }}</span>
                        </el-menu-item>
                    </el-sub-menu>
                    <el-menu-item :index="id" :route="{ name: id }" v-else>
                        <icon :icon="icon" class="mr-4 size-8"></icon><span class="truncate">{{ $t(`title["${id}"]`)
                            }}</span>
                    </el-menu-item>
                </template>
            </el-menu>
        </el-drawer>
    </div>
    <el-backtop></el-backtop>
</template>

<script setup>

import { getCurrentInstance, inject, ref, watch } from "vue";
import { Icon } from "@iconify/vue";
import ElementPlus from "element-plus";
import { createI18n, useI18n } from "vue-i18n";
import { RouterLink } from "vue-router";
import { useRoute } from "vue-router";

const { appContext: { app } } = getCurrentInstance(),
    { id } = defineProps(["id"]),
    pages = inject("pages"),
    i18n = createI18n({
        legacy: false, locale: "ru", fallbackLocale: "en",
        messages: {
            en: {
                title: {
                    "d29e6eb2-4e99-4b4c-b2cc-3ad186ceb4a5": "COMPANY \"VSYA MEDITSINA\"",
                    "5e93a0c9-5d24-45d0-9054-3b75d13d95d8": "COMPANY \"VSYA MEDITSINA\"",
                    "bb905218-7b9d-4f50-8d5f-6e22dbf7d258": "ABOUT THE COMPANY \"VSYA MEDITSINA\"",
                    "76e63b5d-4dda-49ad-80ed-997d6d8b27ff": "SERVICES OF THE COMPANY \"VSYA MEDITSINA\"",
                    "2fc0e0ab-931f-46bb-a29f-d553032bd12d": "TREATMENT AND REHABILITATION OF PATIENTS WITH COVID-19",
                    "90bba0e9-74dd-4a86-9a7b-2b756a526406": "MEDICAL EXAMINATION AND DIAGNOSTICS IN MOSCOW",
                    "3a2d5bf3-0fe3-4215-b062-7e70bcf73620": "HOSPITALIZATION IN MOSCOW",
                    "f29fa02a-021f-4274-9b2f-2777933d7b89": "ASSISTANCE FOR PREVIOUSLY HOSPITALIZED PATIENTS",
                    "afea752e-acd9-4a09-9af5-e3c16098e396": "EMERGENCY MEDICAL CARE AND TRANSPORTATION",
                    "223da248-52eb-4023-afdb-385751ac8ff9": "MEDICAL AIR TRANSPORT",
                    "bc726d5e-1fdc-4d57-b3bd-a03330ab63b4": "MEDICAL REHABILITATION",
                    "a3e82658-b020-42a5-8998-ff69e57d60be": "MEDICAL SUPPORT",
                    "7367f5a9-92dd-435a-8970-50ef1af029ff": "TOP MOSCOW CLINICS",
                    "cd7a7918-ebe7-4632-8fe9-c9d65a9c256a": "CONTACT INFORMATION",
                    "3bb0870f-1887-4ff5-961e-c674e9552cb4": "documents",
                    "0284f2ab-6b1d-41b4-a8d9-815cf6271df2": "USER AGREEMENT",
                    "bc6c8dc5-b7d1-4285-a7db-c85da6acdd3b": "PERSONAL DATA PROCESSING POLICY"
                },
                description: {
                    "d29e6eb2-4e99-4b4c-b2cc-3ad186ceb4a5": "WE WILL HELP YOU NAVIGATE THE WORLD OF MEDICINE.\nSINCE 2013, WE HAVE BEEN COORDINATING MEDICAL SERVICES (DIAGNOSTICS, TREATMENT, REHABILITATION).\nWE WILL SELECT HIGHLY QUALIFIED DOCTORS AND ORGANIZE MEDICAL SUPPORT BASED ON YOUR REQUIREMENTS.",
                    "5e93a0c9-5d24-45d0-9054-3b75d13d95d8": "WE WILL HELP YOU NAVIGATE THE WORLD OF MEDICINE.\nSINCE 2013, WE HAVE BEEN COORDINATING MEDICAL SERVICES (DIAGNOSTICS, TREATMENT, REHABILITATION).\nWE WILL SELECT HIGHLY QUALIFIED DOCTORS AND ORGANIZE MEDICAL SUPPORT BASED ON YOUR REQUIREMENTS.",
                    "bb905218-7b9d-4f50-8d5f-6e22dbf7d258": "DO YOU NEED QUALIFIED MEDICAL CARE FROM TOP MOSCOW, GERMAN, OR ISRAELI CLINICS? CONTACT \"VSYA MEDITSINA\"!",
                    "76e63b5d-4dda-49ad-80ed-997d6d8b27ff": "WE WILL BE HAPPY TO OFFER OUR SERVICES TO HELP RESOLVE ANY HEALTH-RELATED ISSUES",
                    "2fc0e0ab-931f-46bb-a29f-d553032bd12d": "HOSPITALIZATION IN THE MOST COMPETENT AND RELIABLE CLINICAL CENTERS FOR TREATING COVID-19",
                    "90bba0e9-74dd-4a86-9a7b-2b756a526406": "WE WILL DEVELOP AN INDIVIDUAL DIAGNOSTIC PROGRAM BASED ON THE OPTIMAL BALANCE OF COST AND SCOPE OF SERVICES",
                    "3a2d5bf3-0fe3-4215-b062-7e70bcf73620": "WE WILL PROMPTLY RESOLVE ANY QUESTIONS REGARDING THE SELECTION OF A HOSPITAL FOR PLANNED OR EMERGENCY HOSPITALIZATION",
                    "f29fa02a-021f-4274-9b2f-2777933d7b89": "SUPPORT AND SUPERVISION DURING YOUR HOSPITAL STAY",
                    "afea752e-acd9-4a09-9af5-e3c16098e396": "FULL RANGE OF MEDICAL EVACUATION AND PATIENT TRANSPORT SERVICES, INCLUDING FROM ANY REGION OF RUSSIA",
                    "223da248-52eb-4023-afdb-385751ac8ff9": "WE WILL ORGANIZE AIR TRANSPORT FOR THE PATIENT AS QUICKLY AS POSSIBLE TO PROVIDE QUALIFIED MEDICAL CARE",
                    "bc726d5e-1fdc-4d57-b3bd-a03330ab63b4": "SELECTING THE BEST REHABILITATION CENTERS FOR RESTORING HEALTH, FUNCTIONAL STATUS, AND WORK CAPACITY",
                    "a3e82658-b020-42a5-8998-ff69e57d60be": "RESOLVING ALL ORGANIZATIONAL ISSUES FOR THE PATIENT",
                    "7367f5a9-92dd-435a-8970-50ef1af029ff": "WE ORGANIZE TREATMENT BASED ON THE DIAGNOSIS AND INDIVIDUAL CLIENT PREFERENCES IN THE MOST SUITABLE MEDICAL CENTERS",
                    "cd7a7918-ebe7-4632-8fe9-c9d65a9c256a": "APPOINTMENTS ONLY BY PRE-REGISTRATION",
                    "3bb0870f-1887-4ff5-961e-c674e9552cb4": "",
                    "0284f2ab-6b1d-41b4-a8d9-815cf6271df2": "Limited Liability Company \"Vsya Meditsina\"",
                    "bc6c8dc5-b7d1-4285-a7db-c85da6acdd3b": "Limited Liability Company \"Vsya Meditsina\""
                }
            },
            ru: {
                title: Object.fromEntries(Object.entries(pages).map(([key, { title }]) => [key, title])),
                description: Object.fromEntries(Object.entries(pages).map(([key, { description }]) => [key, description])),
            }
        }
    });

app.component("Icon", Icon);
app.use(ElementPlus);
app.use(i18n);

const route = useRoute(),
    the = pages[id],
    drawer = ref(false),
/*    breadcrumbs = computed(() => {
        const branch = pages[route.name].branch.slice(1).map(({ name, to }) => ({ name, to })),
            root = { name: "🏠", to: "/" };
        if (branch.length) branch[0] = root;
        else branch.push(root);
        return branch;
    }),*/
    lang = () => { i18n.global.locale.value = i18n.global.locale.value === "ru" ? "en" : "ru" },
    { t } = useI18n({
        messages: {
            en: {
                0: "circle-flags:ru",
                1: "Компания \"Вся Медицина\"",
                2: "user agreement",
                3: "consent to data processing",
                4: "Moscow",
                5: "Starokirochny Lane, 6",
                6: "view on the map",
                7: "Copyright © All rights reserved. Copying of materials is permitted only with the consent of the website administration. Use of any medical information for personal purposes requires additional consultation with a doctor. All clinics presented on the website hold the appropriate licenses and certificates. All data published on the website http://www.savamed.ru is provided solely for informational purposes, cannot be used as a basis for self-diagnosis or self-treatment, is of an informational nature, and does not constitute a public offer as defined by Part 2 of Article 437 of the Civil Code of the Russian Federation.",
                8: "VueBro is a convenient and flexible tool for managing a website"
            },
            ru: {
                0: "circle-flags:gb",
                1: "Компания \"Вся Медицина\"",
                2: "пользовательское соглашение",
                3: "согласие на обработку данных",
                4: "Москва",
                5: "Старокирочный переулок д. 6",
                6: "посмотреть на карте",
                7: "Copyright © Все права защищены. Копирование материала возможно только с согласия администрации сайта. Использование любой медицинской информации в личных целях требует дополнительной консультации врача. Все клиники, представленные на сайте, имеют соответствующие лицензии и сертификаты. Все данные, опубликованные на сайте http://www.savamed.ru, приведены исключительно для ознакомления, не могут служить поводом для самодиагностики или самолечения, носят информационный характер и не являются публичной офертой, определяемой положениями ч.2 ст.437 Гражданского кодекса РФ.",
                8: "VueBro удобный и гибкий инструмент для управления сайтом"
            }
        }
    });
__unocss_runtime.extract(["truncate", "mr-4", "size-8"]);
watch(() => route.name, () => { drawer.value = false });
</script>

<style scoped>
@import "./node_modules/element-plus/dist/index.css";
@import "./node_modules/animate.css/animate.min.css";
@import "./node_modules/hover.css/css/hover-min.css";

.el-drawer .el-menu {
    border-right: none;
}

#drawer :deep(.el-drawer__body) {
    padding: 0;
}
</style>
