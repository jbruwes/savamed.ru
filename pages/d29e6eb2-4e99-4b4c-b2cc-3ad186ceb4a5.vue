<template>
    <div class="sticky top-0 z-50 pa-4 border-b bg-neutral-50 border-slate-200" ref="pageHeader">
        <el-page-header icon="" :content="pages[$route.name].title" @back="lang">
            <template #breadcrumb>
                <el-breadcrumb separator="/">
                    <el-breadcrumb-item v-for="item in pages[$route.name].branch" :to="item.to">
                        {{ item.name }}
                    </el-breadcrumb-item>
                </el-breadcrumb>
            </template>
            <template #title>
                <div class="text-3xl">{{ t(0) }}</div>
            </template>
            <template #extra>
                <el-button circle @click="drawer = true">
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
                                to="/medicine/contacts/">{{ t(6) }}</el-button>
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
        <el-drawer v-model="drawer" :title="the.header" class="w-full sm:w-96" size="">
            <el-menu :router="true" :default-openeds="[0, 1, 2]">
                <el-sub-menu v-for="({ name, $children, icon }, index) in views" :index="index">
                    <template #title>
                        <icon :icon="icon" class="icon"></icon><span>{{ name }}</span>
                    </template>
                    <el-menu-item v-for="(child, index2) in $children" :route="{ name: child.id }" :index="index2">
                        <icon :icon="child.icon" class="icon"></icon><span>{{ child.name }}</span>
                    </el-menu-item>
                </el-sub-menu>
            </el-menu>
        </el-drawer>
    </div>
    <el-backtop></el-backtop>
</template>

<script setup>

import { getCurrentInstance, inject, ref, computed } from "vue";
import { Icon } from "@iconify/vue";
import ElementPlus from "element-plus";
import { createI18n, useI18n } from "vue-i18n";

const { appContext: { app } } = getCurrentInstance(),
    i18n = createI18n({ legacy: false, locale: "ru", fallbackLocale: "en" });

app.component("Icon", Icon);
app.use(ElementPlus);
app.use(i18n);

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    views = computed(() => the.$children.filter(({ $children }) => $children.length)),
    drawer = ref(false),
    lang = () => { i18n.global.locale.value = i18n.global.locale.value === "ru" ? "en" : "ru" },
    { t } = useI18n({
        messages: {
            en: {
                0: "🇷🇺",
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
                0: "🇬🇧",
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

.icon {
    margin-right: 1rem;
    width: 2rem;
    height: 2rem;
}
</style>
