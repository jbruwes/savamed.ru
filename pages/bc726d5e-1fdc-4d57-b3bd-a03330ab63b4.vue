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
                0: "Comprehensive support to achieve the highest possible level of physical, mental, professional, and social well-being",
                1: "Rehabilitation is a branch of modern medicine that, in its various methods, focuses primarily on the patient as an individual, actively striving to restore bodily functions impaired by illness, as well as the patient’s social connections.",
                2: "Medical rehabilitation is a set of medical and psychological measures aimed at full or partial restoration (compensation) of bodily functions impaired or lost due to an acutely developed pathological process (chronic exacerbation), as well as at preventing or reducing the degree of potential disability, improving quality of life, maintaining the patient’s work capacity, and facilitating their integration into society. Medical rehabilitation is carried out provided the patient’s clinical condition is stable and there is potential for functional recovery (rehabilitation potential).",
                3: "Specialists from \"{t4}\" will select a specialized rehabilitation center in the following areas:",
                4: "Vsya Meditsina",
                list1: [
                    "recovery after injuries",
                    "rehabilitation after cardiovascular diseases",
                    "rehabilitation of patients with mental disorders",
                    "rehabilitation after major internal organ surgeries",
                    "rehabilitation of patients who have lost work capacity due to prolonged or recurrent illnesses",
                    "rehabilitation of patients with complex spinal injuries (spinal patients), intra-articular fractures, crushing of long tubular bones, limb amputations, or congenital absence/underdevelopment of limbs",
                    "rehabilitation of individuals with all disability groups"
                ],
                5: "Our advantages:",
                list2: [
                    "development of an individual rehabilitation program",
                    "selection of the optimal rehabilitation facility (boarding house, sanatorium, rehabilitation center)",
                    "fast service (complete set of necessary tests in 1 day)",
                    "support: supervision and monitoring throughout all stages of rehabilitation",
                    "individual approach"
                ],
                1000: "company services",
                1010: "back to home page"
            },
            ru: {
                0: "Всесторонняя помощь для достижения максимально возможной физической, психической, профессиональной и социальной полноценности",
                1: "Реабилитация – направление современной медицины, которая в своих разнообразных методах опирается, прежде всего, на личность пациента, активно пытаясь восстановить нарушенные болезнью функции человека, а также его социальные связи.",
                2: "Медицинская реабилитация – комплекс мероприятий медицинского и психологического характера, направленных на полное или частичное восстановление (компенсацию) нарушенных либо утраченных функций организма, вследствие остро развившегося патологического процесса (хронического обострения), а также на предупреждение и снижение степени возможной инвалидности, улучшение качества жизни, сохранение работоспособности пациента и его интеграцию в общество. Медицинская реабилитация осуществляется при условии стабильности клинического состояния пациента и наличии перспективы восстановления функций (реабилитационного потенциала).",
                3: "Специалисты компании \"{t4}\" подберут профильный реабилитационный центр по следующим направлениям:",
                4: "Вся Медицина",
                list1: [
                    "восстановление после травм",
                    "реабилитация после перенесенных сердечно-сосудистых заболеваний",
                    "реабилитация психических больных",
                    "реабилитация пациентов, перенесших обширные операции на внутренних органах",
                    "реабилитация пациентов, утративших трудоспособность на фоне длительных и часто повторяющихся заболеваний",
                    "реабилитация пациентов с осложнёнными травмами позвоночного столба (спинальные больные), с внутрисуставными переломами, размозжением длинных трубчатых костей, с ампутацией конечностей или врождённым их отсутствием либо недоразвитием",
                    "реабилитация инвалидов всех групп"
                ],
                5: "Наши преимущества:",
                list2: [
                    "разработка индивидуальной программы реабилитации",
                    "подбор оптимального учреждения реабилитации (пансионат, санаторий, реабилитационный центр)",
                    "быстрое обслуживание (полный комплекс необходимых анализов за 1 день)",
                    "сопровождение: курация, патронаж на всех этапах реабилитации",
                    "индивидуальный подход",
                ],
                1000: "услуги компании",
                1010: "на главную",
            }
        }
    });
</script>