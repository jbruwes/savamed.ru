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
            <el-text tag="p" class="!mb-4 text-justify">{{ t(2) }}</el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="3">
                    <template #t4><strong>{{ t(4) }}</strong></template>
                </i18n-t>
            </el-text>
            <ul class="mb-4">
                <el-text tag="li" v-for="item in tm('list1')" class="list-disc list-inside">{{ item }}</el-text>
            </ul>
        </div>
        <h2>{{ t(5) }}</h2>
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
                    {{ t(6) }}
                </el-button>
                <el-button type="danger" size="large" tag="router-link" to="/">
                    <template #icon>
                        <Icon icon="fa-solid:angle-double-left"></Icon>
                    </template>
                    {{ t(7) }}
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
            },
            ru: {
                0: "Услуги по плановой и экстренной госпитализации с полным медицинским сопровождением на весь период лечения и реабилитации пациентов с COVID-19",
                1: "Коронавирусы – обширное семейство вирусов. Известно, что некоторые из них способны вызывать у человека респираторные инфекции в диапазоне от обычной простуды до более серьёзных состояний.",
                2: "Последний из недавно открытых коронавирусов вызывает заболевание COVID‑19. У большинства заболевших COVID-19 наблюдаются лёгкие или умеренные симптомы, выздоровление происходит без специфического лечения. Однако у некоторых людей заболевание протекает в тяжёлой форме, и им требуется медицинская помощь.",
                3: "Если у Вас или у Ваших близких есть подозрения на болезнь, уже диагностирован COVID‑19 или требуется реабилитация после лечения, Компания \"{t4}\" быстро организует госпитализацию в наиболее компетентные и надёжные в лечении COVID-19 клинические центры:",
                4: "Вся Медицина",
                list1: [
                    "Городская клиническая больница №15 им. О.М.Филатова",
                    "Городская клиническая больница № 67 имени Л.А. Ворохобова",
                    "Городская клиническая больница №52",
                    "Городская клиническая больница № 40",
                    "НИИ СП им Н. В. Склифосовского",
                    "Городская клиническая больница №61 (УКБ №4 первого МГМУ имени И.М.Сеченова)",
                ],
                5: "Наши преимущества:",
                list2: [
                    "госпитализация в экстренные сроки",
                    "подача машины с бригадой скорой помощи в срок до 3-х часов",
                    "доставка пациента из дома в стационар",
                    "гарантированное бережное отношение к пациенту",
                    "индивидуальный подход",
                    "полный комплекс наиболее актуальных методик в лечении COVID-19",
                    "ежедневное отслеживание лечения и состояния пациента",
                    "ежедневный контакт с родственниками"
                ],
                6: "услуги компании",
                7: "на главную",
            }
        }
    });
</script>