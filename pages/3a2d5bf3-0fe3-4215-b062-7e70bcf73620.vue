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
            <el-text tag="p" class="!mb-4 text-justify">{{ t(5) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(6) }}</el-text>
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
                0: "Hospitalization in Leading Moscow Clinics",
                1: "Hospitalization is one of the comprehensive forms of patient care required when, due to health condition or the impossibility of outpatient treatment, a patient needs to stay in a hospital. Planned hospitalization is recommended for complex examinations, round-the-clock therapy under medical supervision, and surgical procedures.",
                2: "Contact the specialists at \"{t3}\" and we will handle all organizational matters for you.",
                3: "Vsya Meditsina",
                4: "We will quickly select the right clinic for you with an individualized treatment approach, arrange hospitalization in a VIP or premium comfort room, and provide full support throughout your treatment period.",
                5: "You can be hospitalized on any day at a time convenient for you.",
                6: "In a hospital setting, patients are under constant supervision by medical specialists and receive attentive care from medical staff.",
                7: "If you are already hospitalized, call us and we will arrange individual monitoring for you at your current clinic.",
                8: "Our advantages:",
                list2: [
                    "selection of top clinics",
                    "diagnosis verification",
                    "detailed treatment plan development",
                    "ensuring your desired comfort level",
                    "support throughout the entire treatment period",
                    "individual approach"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Госпитализация в ведущие клиники Москвы",
                1: "Госпитализация — один из комплексных видов помощи пациенту, когда ему по состоянию здоровья или невозможности проведения лечения в амбулаторно-поликлинических условиях нужно провести какое-то время в стационаре. Планово лечь в стационар стоит, если Вам предстоят сложные исследования, круглосуточная терапия под медицинским наблюдением, а также операции.",
                2: "Обратитесь к специалистам компании \"{t3}\" и мы возьмём на себя все организационные вопросы.",
                3: "Вся Медицина",
                4: "Быстро подберём Вам правильную клинику с индивидуальным подходом в лечении, госпитализируем в vip палату или палату повышенного комфорта, будем сопровождать весь период лечения.",
                5: "Лечь в стационар можно в любой день и в любое удобное для Вас время.",
                6: "В условиях стационара пациенты находятся под постоянным контролем специалистов и окружены вниманием медицинского персонала.",
                7: "Если Вы уже госпитализированы, позвоните нам и мы организуем Вам в этой клинике индивидуальное наблюдение.",
                8: "Наши преимущества:",
                list2: [
                    "подбор лучших клиник",
                    "контроль постановки диагноза",
                    "детальная разработка программы лечения",
                    "обеспечение желаемого Вами уровня комфорта",
                    "сопровождение на протяжении всего периода лечения",
                    "индивидуальный подход"
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>