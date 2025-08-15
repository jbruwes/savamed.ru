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
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="1">
                    <template #t2><strong>{{ t(2) }}</strong></template>
                    <template #t3><strong>{{ t(3) }}</strong></template>
                    <template #t4><strong>{{ t(4) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="5">
                    <template #t6><strong>{{ t(6) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(7) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(8) }}</el-text>
        </div>
        <h2>{{ t(9) }}</h2>
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
                0: "Comprehensive medical examination in Moscow with leading specialists only",
                1: "The company \"{t2}\" continuously collaborates with {t3} medical centers in Moscow and maintains close relationships with doctors, including {t4} top specialists, professors, department heads, doctors of science, and physicians of international reputation.",
                2: "Vsya Meditsina",
                3: "leading",
                4: "best",
                5: "Over the years of cooperation, we have helped our clients navigate the world of medicine, organized hundreds of examinations and hospitalizations, and consistently monitored, analyzed doctors' work, tracked treatment quality, and defended clients' interests. As a result, we have built a network of partner specialists practicing in various state clinics across Moscow, and each of our partners is a {t6} in their field, well-versed in communication ethics, and brings a unique approach to patient care.",
                6: "true professional",
                7: "Examinations are performed only on state-of-the-art equipment. All tests are conducted in the best clinical and diagnostic laboratories. Many of our specialists are also actively involved in scientific research, holding Candidate or Doctor of Medical Sciences degrees, studying pathological conditions, and publishing their findings annually in peer-reviewed scientific journals.",
                8: "Upon completion of your examination, you will receive complete information about your health status, including a detailed description of all identified issues and recommendations for further treatment and disease prevention.",
                9: "Our advantages:",
                list2: [
                    "rapid appointment scheduling",
                    "full-body examination (CHECK-UP) in one day",
                    "laboratory and instrumental diagnostics of any complexity",
                    "personal support throughout the entire examination period",
                    "comprehensive information about your health status",
                    "individual approach",
                    "guaranteed high quality and speed"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Полное медицинское обследование в Москве только у профильных специалистов",
                1: "Компания \"{t2}\" постоянно сотрудничает с {t3} медицинскими центрами Москвы, поддерживает тесные связи с докторами, среди которых {t4} профильные специалисты, профессора, заведующие отделениями клиник, доктора наук и врачи с мировым именем.",
                2: "Вся Медицина",
                3: "ведущими",
                4: "лучшие",
                5: "За годы сотрудничества мы помогали нашим клиентам сориентироваться в мире медицины, организовали сотни обследований и госпитализаций и всегда внимательно наблюдали, анализировали работу врачей, отслеживали качество лечения, отстаивали интересы клиентов. В результате мы сформировали коллектив партнёров, врачей-специалистов, которые практикуют в различных государственных клиниках Москвы и каждый наш партнёр – {t6} в своей специальности, хорошо осведомлён в вопросах этики общения, а также имеет индивидуальный акцент в своей работе.",
                6: "истинный профессионал",
                7: "Обследования проводятся только на высокотехнологичном оборудовании. Все исследования проводятся в лучших клинико-диагностических лабораториях. Многие специалисты также занимаются научной работой, являются кандидатами и докторами медицинских наук, исследуют вопросы патологий и ежегодно публикуют результаты работы в рецензируемых научных изданиях.",
                8: "По результатам прохождения обследования Вы получите полную информацию о состоянии Вашего здоровья с подробным описанием всех выявленных проблем и рекомендациями по дальнейшему лечению и профилактике заболеваний.",
                9: "Наши преимущества:",
                list2: [
                    "организация консультаций в кратчайшие сроки",
                    "полное обследование организма (CHECK-UP) за один день",
                    "лабораторная и аппаратная диагностика любой сложности",
                    "сопровождение на протяжении всего периода обследования",
                    "комплексная информация о состоянии Вашего здоровья",
                    "индивидуальный подход",
                    "гарантированное качество и быстрота"
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>