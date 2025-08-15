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
            <el-text tag="p" class="!mb-4 text-justify">{{ t(3) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(4) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(5) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(6) }}</el-text>
        </div>
        <h2>{{ t(7) }}</h2>
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
                0: "Air transportation is the fastest, most reliable, and safest option",
                1: "No matter where you are — on vacation, at work, or at home — an accident or sudden illness can happen at any moment. Within just a few hours, we can deliver you or your loved ones to one of the best clinics in Europe.",
                2: "Air ambulance services — flights accompanied by qualified medical personnel with all necessary equipment.",
                3: "Before the flight: the doctor reviews all critical medical data prior to accepting the patient.",
                4: "During the flight: medical personnel, including a doctor and assistant, provide continuous care for the patient.",
                5: "We handle all coordination with administrative authorities, consulates, and clinics, ensuring service at the highest level.",
                6: "We understand how precious every minute can be. In emergencies, we are ready to transport patients from the European part of Russia to a specialized European medical center within several hours!",
                7: "Our advantages:",
                list2: [
                    "rapid organization of patient transportation",
                    "arrangement of optimal medical care before, during, and after the flight",
                    "professional selection of the best specialized medical facility for emergency admission",
                    "organization of accompanying medical support at the treatment location",
                    "optimal balance of service cost and quality"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Авиационная транспортировка — максимально быстрая, надёжная и безопасная",
                1: "Где бы Вы ни находились: в отпуске, на работе или дома, несчастный случай или внезапное заболевание – всё может произойти. В считанные часы мы поможем доставить Вас или Ваших близких в одну из лучших клиник Европы.",
                2: "Авиационная скорая помощь – рейсы в сопровождении квалифицированного медицинского персонала с необходимым оборудованием.",
                3: "Перед полётом: перед приёмом пациента врач знакомится со всеми важными медицинскими показателями.",
                4: "В ходе полёта: медицинский персонал, в который входит врач и ассистент, заботится о пациенте.",
                5: "Урегулируем все вопросы с административными органами, консульствами и клиниками, обеспечим обслуживание на самом высоком уровне.",
                6: "Мы знаем, как порою дорога каждая минута времени. В экстренных случаях мы готовы доставить наших пациентов из европейской части России в течение нескольких часов в профильный европейский медицинский центр!",
                7: "Наши преимущества:",
                list2: [
                    "быстрая организация транспортировки пациента",
                    "организация лучшего медицинского обеспечения до, во время перелёта и по месту прибытия",
                    "квалифицированный подбор лучшего профильного медицинского учреждения для приема экстренного больного",
                    "организация сопровождающего медицинского сервиса по месту лечения",
                    "оптимальное соотношение цены и качества наших услуг",
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>