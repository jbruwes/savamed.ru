<template>
    <div class="my-12 mx-auto w-fit text-center" un-cloak>
        <img class="w-48" :title="t(0)" :src="logoUrl" :alt="t(0)">
        <div><el-link href="tel:+79151797755" underline="never">+7 (915) 179-77-55</el-link></div>
    </div>
    <div :class="`bg-[url(${the.images[0].url})]`" class="min-h-[70dvh] bg-center bg-cover flex" un-cloak>
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
    <div class="container mx-auto my-12 px-2 sm:px-none">
        <h2>{{ t(2) }}</h2>
        <div class="not-prose">
            <el-text tag="p" class="!mb-4">{{ t(3) }}</el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="4">
                    <template #t5><strong>{{ t(5) }}</strong></template>
                    <template #t6><strong>{{ t(6) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="7">
                    <template #t8>
                        <el-button link class="!pa-0 !border-0 !align-baseline" tag="router-link" type="danger"
                            to="/services/">{{ t(8) }}</el-button>
                    </template>
                    <template #t9>
                        <el-button link class="!pa-0 !border-0 !align-baseline !ml-0" tag="router-link" type="danger"
                            to="/support/">{{ t(9) }}</el-button>
                    </template>
                </i18n-t>
            </el-text>
            <el-text class="!mb-4">{{ t(10) }}</el-text>
        </div>
        <div class="not-prose mt-12"><el-button type="danger" size="large" tag="router-link" to="/about/">{{
            t(11)
                }}&nbsp;<Icon icon="fa-solid:angle-right" class="size-7"></Icon></el-button></div>
        <div class="my-12"><el-divider></el-divider></div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 not-prose">
            <UseElementVisibility v-slot="{ isVisible }" v-for="{ icon, to, id } in childfree" :key="id" class="text-center">
                <router-link :to="to" class="text-center ma-4 hvr-icon-wobble-vertical animate__animated"
                    :class="{ animate__slideInUp: isVisible, animate__slideOutDown: !isVisible, }">
                    <Icon :icon="icon" class="size-15 text-teal-700 mb-4 hvr-icon mx-auto"></Icon>
                    <div>{{ $t(`title["${id}"]`) }}</div>
                </router-link>
            </UseElementVisibility>
        </div>
    </div>
    <el-carousel height="80dvh" arrow="always" autoplay class="my-28" indicator-position="none" un-cloak>
        <el-carousel-item v-for="{ images: [{ url }], icon, to, id } in the.parent.$children.slice(1)" :key="id"
            :class="`bg-[url(${url})]`" class="min-h-[70dvh] bg-center bg-cover !flex">
            <div class="flex-auto bg-black/50 flex items-center">
                <div class="container mx-auto text-white flex flex-col items-center text-center gap-4">
                    <router-link :to="to" class="no-underline">
                        <div class="hvr-icon-wobble-vertical my-2">
                            <Icon :icon="icon" class="size-24 hvr-icon"></Icon>
                        </div>
                        <h1>{{ $t(`title["${id}"]`) }}</h1>
                        <p>{{ $t(`description["${id}"]`) }}</p>
                    </router-link>
                </div>
            </div>
        </el-carousel-item>
    </el-carousel>
    <div class="container mx-auto grid gap-12 my-24 grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 px-2 lg:px-none" un-cloak>
        <UseElementVisibility v-slot="{ isVisible }" v-for="{ images: [{ url }], to, icon, id } in services.$children" :key="id"
            class="not-prose flex">
            <el-card class="animate__animated animate__faster w-full"
                :class="{ animate__zoomIn: isVisible, animate__zoomOut: !isVisible, }" body-class="!pa-0 flex"
                shadow="hover">
                <div @mouseover="slide[id] = true" @mouseleave="slide[id] = false" :class="`bg-[url(${url})]`"
                    class="flex flex-auto h-64 bg-center bg-cover overflow-hidden">
                    <transition enter-active-class="animate__animated animate__slideInUp animate__faster"
                        leave-active-class="animate__animated animate__slideOutUp animate__faster">
                        <router-link v-show="slide[id]" class="bg-white/85 flex-auto flex justify-center items-center"
                            :to="to">
                            <el-button size="large" circle="" tag="router-link" :to="to">
                                <icon :icon="icon"></icon>
                            </el-button>
                        </router-link>
                    </transition>
                </div>
                <template #footer>
                    <router-link class="flex flex-col items-start gap-4 lg:flex-row" :to="to">
                        <div class="flex items-center hvr-icon-wobble-vertical">
                            <icon :icon="icon" class="size-7 hvr-icon"></icon>
                        </div>
                        <div class="flex flex-col items-start justify-center w-full min-w-0 gap-0 text-base">
                            <h3 class="mb-4 text-lg leading-6 text-slate-700">{{ $t(`title["${id}"]`) }}</h3>
                            <p class="text-slate-500">{{ $t(`description["${id}"]`) }}</p>
                        </div>
                    </router-link>
                </template>
            </el-card>
        </UseElementVisibility>
    </div>
</template>

<script setup lang="js">
import { inject, reactive } from "vue";
import { useI18n } from "vue-i18n";
import { UseElementVisibility } from "@vueuse/components";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    childfree = Object.values(pages).filter(({ children, enabled }) => enabled && children.length === 0).slice(1),
    services = Object.values(pages).find(({ name }) => name === "services"),
    slide = reactive({}),
    { url: logoUrl } = the.images.find(({ alt }) => alt === "логотип"),
    { t } = useI18n({
        messages: {
            en: {
                2: "The specificity of our work is the coordination of medical services",
                3: "A recent survey by the market research agency IPSOS showed that three out of four residents of our country lack access to quality medical services. Insufficient healthcare funding has led to a shortage of personnel, increased workload for medical professionals, unequal access to qualified medical care across regions, and treatment is typically \"prescribed\" by manufacturers of medications and medical equipment.",
                4: "And when health problems arise, people feel lost and don't know what to do. To avoid wasting time, nerves, and money, contact the {t5} \"{t6}\".",
                5: "company",
                6: "Vsya Meditsina",
                7: "Since 2013, the Company has been engaged in coordinating {t8} (diagnostics, treatment, rehabilitation) and organizing {t9}.",
                8: "medical services",
                9: "medical support",
                10: "The employees of \"Vsya Meditsina\" are guides in the world of medical services. Through our staff, each client receives, for the duration of our support and supervision, not only a family doctor, but also an advocate, an influential manager, and a translator from medical terminology into plain Russian. We will resolve all issues related to diagnosis, treatment, and hospitalization.",
                11: "about us",
            },
            ru: {
                2: "Специфика нашей работы - координация медицинских услуг",
                3: "Недавний опрос агентства маркетинговых исследований IPSOS показал, что трое из четырёх жителей нашей страны лишены доступа к качественным медицинским услугам. Недостаток финансирования здравоохранения привёл к дефициту кадров, повышенной нагрузке на медиков, неравенству в доступе к квалифицированной медицинской помощи в регионах, а лечение \"назначают\", как правило, производители медикаментов и оборудования.",
                4: "И когда возникают проблемы со здоровьем, люди теряются и не знают что делать. Чтобы не тратить время, нервы и деньги, обратитесь в {t5} \"{t6}\".",
                5: "Компанию",
                6: "Вся медицина",
                7: "С 2013 года Компания занимается координацией {t8} (диагностика, лечение, реабилитация) и организацией {t9}.",
                8: "медицинских услуг",
                9: "медицинского сопровождения",
                10: "Сотрудники компании \"Вся медицина\" - проводники в мире медицинских услуг. В лице сотрудника компании каждый клиент получает, на время нашей работы по сопровождению и курации, и семейного доктора, и адвоката, и влиятельного менеджера, и переводчика с медицинского на русский. Решим все вопросы по диагностике, лечению, госпитализации.",
                11: "о нас",
            }
        }
    });
</script>