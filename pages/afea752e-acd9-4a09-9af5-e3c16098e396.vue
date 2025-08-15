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
                0: "Timely and high-quality medical care helps preserve health",
                1: "The patient's condition, and sometimes even their life, depends on how quickly the emergency medical team arrives. Accurate diagnosis during the initial examination by an emergency doctor determines all further actions of the medical staff and the appropriateness of the prescribed treatment. Therefore, it is important to turn to experienced specialists who can promptly provide all necessary assistance.",
                2: "Patient transportation to a hospital with medical accompaniment is often required even during planned hospitalization.",
                3: "Contact the specialists at \"{t4}\", and we will promptly arrange hospitalization in a specialized medical facility in Moscow based on the diagnosis and severity of the condition, including from any region of Russia.",
                4: "Vsya Meditsina",
                5: "You can always count on us. We will fully take over all matters related to patient transportation.",
                6: "No matter what happens, remain calm until the doctors arrive, maintain verbal and visual contact with the patient. If necessary, answer the arriving team's questions and do not interfere with the provision of emergency care. Every second counts!",
                7: "Our advantages:",
                list2: [
                    "urgent processing of all required documents",
                    "on-site specialist consultations",
                    "pre-trip and post-trip medical examinations",
                    "transportation of critically ill and intensive care patients",
                    "resuscitation teams equipped with modern medical equipment",
                    "support throughout the entire treatment period",
                    "individual approach"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Качественная и своевременно оказанная медицинская помощь помогает спасти здоровье",
                1: "От того насколько быстро приедет бригада скорой помощи зависит состояние, а иногда и жизнь человека. Верная постановка диагноза при первичном осмотре больного врачом скорой помощи, определяет все дальнейшие действия медперсонала, а также адекватность назначенного лечения. Поэтому важно обратиться к опытным специалистам, которые будут способны оперативно оказать всю необходимую помощь.",
                2: "Транспортировка пациента в больницу с медицинским сопровождением часто бывает необходима и при плановой госпитализации.",
                3: "Обратитесь к специалистам компании \"{t4}\" и мы оперативно разместим пациента в профильный стационар Москвы с учётом диагноза и тяжести состояния, в том числе из любого региона России.",
                4: "Вся Медицина",
                5: "Вы всегда можете на нас рассчитывать. Полностью возьмём на себя решение всех вопросов по транспортировке пациента.",
                6: "Чтобы ни случилось, до приезда врачей, сохраняйте спокойствие, поддерживайте устную и визуальную связь с пострадавшим. При необходимости, отвечайте на вопросы прибывшей бригады и не препятствуйте оказанию первой помощи. На счету бывает каждая секунда!",
                7: "Наши преимущества:",
                list2: [
                    "оформление всех необходимых документов в экстренном порядке",
                    "выездные консультации специалистов",
                    "предрейсовые и послерейсовые осмотры",
                    "перевозка реанимационных больных и в критическом состоянии",
                    "реанимационные бригады укомплектованы современным оборудованием",
                    "сопровождение на протяжении всего периода лечения",
                    "индивидуальный подход"
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>