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
    <div class="container mx-auto my-12 px-2 sm:px-none" un-cloak>
        <h1 class="text-center">{{ t(0) }}</h1>
        <div class="not-prose my-12">
            <el-text tag="p" class="!mb-4 text-justify">{{ t(1) }}</el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="2">
                    <template #t3><strong>{{ t(3) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(4) }}</el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="5">
                    <template #t6><strong>{{ t(6) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(7) }}</el-text>
        </div>
        <h2>{{ t(8) }}</h2>
        <div class="not-prose my-4">
            <ul class="mb-4 list-none divide-y divide-gray-300">
                <el-text tag="li" v-for="item in tm('list2')"
                    class="relative !pa-6 before:absolute before:left-0 before:content-['✅']" size="large">{{ item
                    }}</el-text>
            </ul>
        </div>
        <div class="not-prose mt-12">
            <el-button-group>
                <el-button type="danger" size="large" tag="router-link" to="/services/">
                    <template #icon>
                        <Icon icon="fa-solid:angle-left"></Icon>
                    </template>
                    {{ t(1000) }}
                </el-button>
                <el-button type="danger" size="large" tag="router-link" to="/">
                    <template #icon>
                        <Icon icon="fa-solid:angle-double-left"></Icon>
                    </template>
                    {{ t(1010) }}
                </el-button></el-button-group>
        </div>
    </div>
</template>

<script setup lang="js">
import { inject } from "vue";
import { useI18n } from "vue-i18n";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    { t, tm } = useI18n({
        messages: {
            en: {
                0: "Your health is our concern and top priority",
                1: "Imagine the following situation: a patient is admitted by ambulance to an unfamiliar hospital ward. The examination and treatment are mediocre or even inadequate, and the competence of the medical staff inspires distrust or raises questions. There is no progress toward recovery...",
                2: "The company \"{t3}\" will come to the rescue even in this situation.",
                3: "Vsya Meditsina",
                4: "Support and monitoring of previously hospitalized patients is another area of our work.",
                5: "The experience and expertise of the company \"{t6}\" enable us to organize supervision and round-the-clock monitoring for patients already in medical facilities, and to oversee medical procedures during diagnosis, treatment, or rehabilitation.",
                6: "Vsya Meditsina",
                7: "Upon receiving a client's request, our staff immediately begin handling organizational matters.",
                8: "Our advantages:",
                list2: [
                    "prompt resolution of organizational issues",
                    "if necessary, quick transfer to another hospital",
                    "guaranteed careful and respectful treatment of the patient",
                    "ensuring the desired comfort level",
                    "daily monitoring of treatment and patient condition",
                    "daily contact with relatives"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Ваше здоровье — наша забота и главный приоритет",
                1: "Представьте ситуацию: пациента госпитализируют на \"скорой\" в незнакомый больничный стационар. Обследование и лечение, при этом, посредственные, либо вовсе неадекватные, компетенция медицинского персонала вызывает недоверие или вопросы. Сдвигов в сторону выздоровления нет...",
                2: "Компания \"{t3}\" придёт на помощь и в этой ситуации.",
                3: "Вся Медицина",
                4: "Сопровождение и контроль ранее госпитализированных пациентов — ещё одно направление в нашей работе.",
                5: "Опыт и наработки компании \"{t6}\" помогают организовать сопровождение и круглосуточное наблюдение пациентов, уже находящихся в лечебных учреждениях, контролировать медицинские манипуляции на этапах обследования, лечения или реабилитации.",
                6: "Вся медицина",
                7: "После клиентского обращения наши сотрудники незамедлительно приступают к организационным вопросам.",
                8: "Наши преимущества:",
                list2: [
                    "оперативное решение организационных вопросов",
                    "при необходимости быстрый перевод в другой стационар",
                    "гарантированное бережное отношение к пациенту",
                    "обеспечение желаемого Вами уровня комфорта",
                    "ежедневное отслеживание лечения и состояния пациента",
                    "ежедневный контакт с родственниками",
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>