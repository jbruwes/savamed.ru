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
                    <template #t7><strong>{{ t(7) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(8) }}</el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="9">
                    <template #t10><strong>{{ t(10) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="11">
                    <template #t12>
                        <el-button link class="!pa-0 !border-0 !align-baseline" tag="router-link" type="danger"
                            to="/medicine/clinics/">{{ t(12) }}</el-button>
                    </template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(13) }}</el-text>
            <ul class="mb-4">
                <el-text tag="li" v-for="item in tm('list1')" class="list-disc list-inside">{{ item }}</el-text>
            </ul>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(14) }}</el-text>
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
                "0": "Your Personal Physician-Coordinator",
                "1": "When a person becomes ill, they naturally turn to a doctor, hoping that a qualified specialist will determine what has happened and how to restore their health. This is the ideal scenario. But what if your experience tells you that true professionals among doctors are few, that doctors are often preoccupied with personal concerns rather than protecting the patient’s interests, that treatment is prescribed not by doctors but by manufacturers of medications and equipment, and that the internet is flooded with fake ratings and fabricated reviews?",
                "2": "What should you do if you are not a doctor yourself? How can you avoid getting lost in the medical world and find exactly the right doctor who can help? Where and how can you find a medical support service?",
                "3": "The company \"{t4}\" organizes disease diagnostics and treatment, acting as your \"{t5}\" throughout the entire course of therapy.",
                "4": "Vsya Meditsina",
                "5": "medical coordinator",
                "6": "Our company's specialists become your \"{t7}\". Being highly qualified doctors and medical service organizers, our staff accompany every step you take and strictly safeguard your interests throughout the examination and treatment process!",
                "7": "medical advocate",
                "8": "This practice is well known throughout the civilized world, and such specialists are called physician-coordinators.",
                "9": "Over the years, the employees of \"{t10}\" have accumulated a comprehensive database of state hospitals and private clinics, as well as individual highly qualified doctors, regardless of which clinic they currently work in.",
                "10": "Vsya Meditsina",
                "11": "Our primary focus is on your health! Today, advanced equipment is no longer a rarity. But we {t12} where specialists know how to fully leverage the potential of the latest technologies 100% in the patient’s interest.",
                "12": "select diagnostic centers and clinics",
                "13": "To make it easier for you to understand, here are some examples:",
                "14": "We always request feedback from our clients who have undergone treatment. And these reviews are typically positive!",
                "list1": [
                    "there are many cardiologists in Moscow, but far fewer true professionals, and only a handful who have deeply and thoroughly studied the issue of arrhythmias",
                    "most urologists can break kidney stones, but the number of specialists whom urologists themselves turn to for help when facing stone-related issues can be counted on one hand",
                    "there are many obstetrician-gynecologists in Moscow, but the number of doctors with a flawless track record is very limited, and knowing this track record is a safe path to health"
                ],
                "15": "back to home page"
            },
            ru: {
                0: "Ваш личный врач—координатор",
                1: "Когда человек заболевает, он, естественно, обращается к врачу в надежде, что квалифицированный специалист определит, что произошло и каким образом можно помочь восстановить здоровье. Это в норме. А если Ваш опыт говорит о том, что профессионалов в среде врачей не так много, что врачи часто озабочены личными проблемами, а не защитой интересов пациента, что лечение \"назначают\" не врачи, а производители медикаментов и оборудования, а интернет переполнен искусственными рейтингами и выдуманными отзывами?",
                2: "Что же делать, если Вы при этом не врач? Как не потеряться в медицинском мире и найти именно того врача, который сможет помочь? Где и как найти службу медицинского сопровождения?",
                3: "Компания \"{t4}\" занимается организацией диагностики заболеваний и лечения, выступая в качестве Вашего \"{t5}\" в течение всего курса терапии.",
                4: "Вся медицина",
                5: "медицинского сопровождающего",
                6: "Специалисты нашей компании становятся Вашим \"{t7}\". Будучи высококвалифицированными врачами и организаторами медицинского обслуживания, наши сотрудники сопровождают каждый Ваш шаг и строго следят за соблюдением Ваших интересов в процессе прохождения обследования и лечения!",
                7: "медицинским адвокатом",
                8: "Такая практика хорошо известна во всём цивилизованном мире, а таких специалистов называют врачами-координаторами.",
                9: "За годы работы сотрудниками компании \"{t10}\" накоплена база данных о государственных больницах и частных клиниках, об отдельных высококвалифицированных врачах, вне зависимости от того, в какой клинике они сейчас работают.",
                10: "Вся медицина",
                11: "Мы исходим, в первую очередь, из интересов Вашего здоровья! Новым оборудованием сегодня уже мало кого удивишь. Но мы {t12}, в которых специалисты умеют использовать возможности новейших технологий на все 100% в интересах пациента.",
                12: "выбираем диагностические центры и клиники",
                13: "Чтобы Вам было проще разобраться приведём примеры:",
                14: "Мы в обязательном порядке запрашиваем отзывы от своих клиентов, прошедших лечение. И, как правило, эти отзывы оказываются положительными!",
                list1: [
                    "кардиологов в Москве очень много, истинных профессионалов гораздо меньше, а специалистов, максимально глубоко изучивших проблему аритмий – единицы",
                    "большинство урологов умеют дробить камни в почках, но специалистов, к которым обращаются сами урологи за помощью, в случае возникновения проблем с камнями можно пересчитать по пальцам",
                    "акушеров-гинекологов в Москве очень много, но количество врачей с идеальной статистикой работы весьма ограничено и знание этой статистики – безопасный путь к здоровью",
                ],
                15: "на главную"
            }
        }
    });
</script>