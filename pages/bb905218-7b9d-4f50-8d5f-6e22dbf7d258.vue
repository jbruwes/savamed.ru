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
                    <template #t5><strong>{{ t(5) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="6">
                    <template #t7>
                        <el-button link class="!pa-0 !border-0 !align-baseline" tag="router-link" type="danger"
                            to="/medicine/services/">{{ t(7) }}</el-button>
                    </template>
                    <template #t8>
                        <el-button link class="!pa-0 !border-0 !align-baseline !ml-0" tag="router-link" type="danger"
                            to="/medicine/support/">{{ t(8) }}</el-button>
                    </template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="9">
                    <template #t10><strong>{{ t(10) }}</strong></template>
                </i18n-t>
            </el-text>
            <ul class="mb-4">
                <el-text tag="li" v-for="item in tm('list1')" class="list-disc list-inside">{{ item }}</el-text>
            </ul>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(11) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(12) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(13) }}</el-text>
        </div>
        <h2>{{ t(14) }}</h2>
        <div class="not-prose my-4">
            <ul class="mb-4 list-none divide-y divide-gray-300">
                <el-text tag="li" v-for="item in tm('list2')"
                    class="relative !pa-6 before:absolute before:left-0 before:content-['✅']" size="large">{{ item
                    }}</el-text>
            </ul>
        </div>
        <div class="not-prose mt-12"><el-button type="danger" size="large" tag="router-link" to="/">
                <template #icon>
                    <Icon icon="fa-solid:angle-double-left"></Icon>
                </template>
                {{ t(15) }}
            </el-button></div>
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
                "0": "The focus of our work is the coordination of medical services.",
                "1": "A recent survey by the IPSOS marketing research agency showed that three out of four residents of our country lack access to quality medical services. Insufficient healthcare funding has led to a shortage of personnel, increased workload for medical professionals, unequal access to qualified medical care across regions, and treatment is typically prescribed by manufacturers of medications and medical equipment.",
                "2": "And when health problems arise, people feel lost and don't know what to do.",
                "3": "To avoid wasting time, nerves, and money, contact {t4} \"{t5}\".",
                "4": "the company",
                "5": "Vsya Meditsina",
                "6": "Since 2013, the company has been coordinating {t7} (diagnostics, treatment, rehabilitation) and organizing {t8}.",
                "7": "medical services",
                "8": "medical support",
                "9": "Over the years of cooperation with most medical institutions in Moscow, we have built a {t10} working in institutions such as:",
                "10": "database of specialists",
                "list1": [
                    "I.M. Sechenov First Moscow State Medical University",
                    "Central Clinical Hospital No. 1 of the Presidential Executive Office",
                    "Central Clinical Hospital \"RZD-Medicine\"",
                    "N.N. Burdenko National Medical Research Center of Neurosurgery",
                    "National Medical Research Center of Cardiology of the Ministry of Health of the Russian Federation",
                    "Central Clinical Hospital of the Russian Academy of Sciences",
                    "V.P. Serbsky National Medical Research Center of Psychiatry and Narcology",
                    "Research Institute of Emergency Children's Surgery and Traumatology",
                    "National Medical Research Center of Endocrinology of the Ministry of Health of the Russian Federation",
                    "V.F. Snegirev Maternity and Gynecology Clinic",
                    "P.A. Gertsen Moscow Oncology Research Institute, a branch of the FSBI National Medical Research Center of Radiology of the Ministry of Health of the Russian Federation, and others."
                ],
                "11": "Over the years of operation, we have organized hundreds of examinations and hospitalizations, carefully monitoring, analyzing doctors' work, tracking treatment quality, and defending clients' interests. As a result, we have formed a network of our partner physicians practicing in various state clinics in Moscow. Each of our partners is a true professional in their field, well-versed in medical ethics and communication, and brings a unique approach to patient care.",
                "12": "The employees of \"Vsya Meditsina\" are guides in the world of medical services, holding higher medical education and possessing both clinical and administrative experience.",
                "13": "Through our staff, each client receives, during our support and care period, a family doctor, an advocate, an influential manager, and a translator from medical jargon into plain Russian. We will resolve all issues related to diagnosis, treatment, and hospitalization.",
                "14": "For our clients:",
                "list2": [
                    "individual approach",
                    "fast service (full diagnostic package and hospitalization within one day)",
                    "comprehensive support (care and supervision throughout all stages: diagnosis, treatment, rehabilitation)",
                    "arranging assistance in any medical institution of interest to you",
                    "second opinion (involving external specialists in complex cases or when there are doubts about the diagnosis or treatment plan)",
                    "VIP medical check-ups for your company's employees"
                ],
                "15": "back to home page"
            },
            ru: {
                0: "Специфика нашей работы - координация медицинских услуг",
                1: "Недавний опрос агентства маркетинговых исследований IPSOS показал, что трое из четырёх жителей нашей страны лишены доступа к качественным медицинским услугам. Недостаток финансирования здравоохранения привёл к дефициту кадров, повышенной нагрузке на медиков, неравенству в доступе к квалифицированной медицинской помощи в регионах, а лечение \"назначают\", как правило, производители медикаментов и оборудования.",
                2: "И когда возникают проблемы со здоровьем, люди теряются и не знают что делать.",
                3: "Чтобы не тратить время, нервы и деньги, обратитесь в {t4} \"{t5}\".",
                4: "Компанию",
                5: "Вся медицина",
                6: "С 2013 года Компания занимается координацией {t7} (диагностика, лечение, реабилитация) и организацией {t8}.",
                7: "медицинских услуг",
                8: "медицинского сопровождения",
                9: "За годы сотрудничества с большинством лечебных учреждений Москвы мы сформировали {t10}, работающих в таких учреждениях, как:",
                10: "базу специалистов",
                list1: [
                    "Первый Московский государственный медицинский университет имени И.М.Сеченова",
                    "ЦКБ №1 управления делами Президента",
                    "ЦКБ \"РЖД-Медицина\"",
                    "Национальный медицинский исследовательский центр нейрохирургии имени академика Н.Н.Бурденко",
                    "Национальный медицинский исследовательский центр кардиологии Минздрава России",
                    "Центральная клиническая больница Российской академии наук",
                    "Национальный медицинский исследовательский центр психиатрии и наркологии имени В.П.Сербского",
                    "Научно-исследовательский институт неотложной детской хирургии и травматологии",
                    "Национальный медицинский центр эндокринологии Минздрава России",
                    "Клиника акушерства и гинекологии имени В.Ф.Снегирева",
                    "МНИОИ им. П.А.Герцена, филиал ФГБУ НМИЦ радиологии Минздрава России и др."
                ],
                11: "За время работы мы организовали сотни обследований и госпитализаций и всегда внимательно наблюдали, анализировали работу врачей, отслеживали качество лечения, отстаивали интересы клиентов. В результате мы сформировали коллектив наших партнёров, врачей-специалистов, которые практикуют в различных государственных клиниках Москвы и каждый наш партнёр &ndash; истинный профессионал в своей специальности, хорошо осведомлён в вопросах этики общения, а также имеет индивидуальный акцент в работе.",
                12: "Сотрудники компании \"Вся медицина\" - проводники в мире медицинских услуг, имеют высшее медицинское образование и опыт работы как клинический, так и административный.",
                13: "В лице сотрудника компании каждый клиент получает, на время нашей работы по сопровождению и курации, и семейного доктора, и адвоката, и влиятельного менеджера, и переводчика с медицинского на русский. Решим все вопросы по диагностике, лечению, госпитализации.",
                14: "Для наших клиентов:",
                list2: [
                    "индивидуальный подход",
                    "быстрое обслуживание (полный комплекс диагностики и госпитализация за 1 день)",
                    "сопровождение (курация, патронаж на всех этапах диагностики, лечения, реабилитации)",
                    "организация помощи в любом интересующем Вас медицинском учреждении",
                    "\"второе мнение\" (привлечение сторонних специалистов в сложных случаях или при наличии сомнений в правильности постановки диагноза или выбора методов лечения)",
                    "VIP–диспансеризация для сотрудников Вашей компании"
                ],
                15: "на главную"
            }
        }
    });
</script>