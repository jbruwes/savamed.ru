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
    <div class="container mx-auto my-12 px-2 sm:px-none overflow-hidden" un-cloak>
        <h1 class="text-center">{{ t(0) }}</h1>
        <div class="not-prose my-12">
            <el-text tag="p" class="!mb-4">
                <i18n-t keypath="1">
                    <template #t3><strong>{{ t(2) }}</strong></template>
                </i18n-t>
            </el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(3) }}</el-text>
            <el-text tag="p" class="!mb-4 text-justify">{{ t(4) }}</el-text>
        </div>
        <h2>{{ t(5) }}</h2>
        <div class="divide-y divide-gray-300 not-prose">
            <UseElementVisibility v-slot="{ isVisible }" v-for="({ title, description, to }, i) in tm('list1')">
                <div class="my-4 flex flex-col items-start gap-4 sm:flex-row animate__animated animate__faster"
                    :class="{ animate__fadeInRight: isVisible, invisible: !isVisible }">
                    <div @mouseover="slide[i] = true" @mouseleave="slide[i] = false"
                        :class="`bg-[url(${the.images[i + 1].url})]`"
                        class="flex w-full h-48 sm:w-48 sm:h-24 bg-center bg-cover overflow-hidden rounded">
                        <transition enter-active-class="animate__animated animate__slideInUp animate__faster"
                            leave-active-class="animate__animated animate__slideOutUp  animate__faster">
                            <a v-if="slide[i]" class="bg-white/85 flex-auto flex justify-center items-center" :href="to"
                                target="_blank" rel="noopener noreferrer">
                                <el-button size="large" circle="" tag="a" :href="to" target="_blank"
                                    rel="noopener noreferrer">
                                    <icon icon="fa-solid:hospital"></icon>
                                </el-button>
                            </a>
                        </transition>
                    </div>
                    <a :href="to" class="!flex w-full min-w-0 gap-4 text-base group" target="_blank"
                        rel="noopener noreferrer">
                        <div class="flex flex-col items-start justify-center w-full min-w-0 gap-0 text-base">
                            <el-text size="large" tag="b" class="mb-4 w-full group-hover:text-sky-800">
                                {{ title }}
                            </el-text>
                            <el-text class="w-full">{{ description }}</el-text>
                        </div>
                    </a>
                </div>
            </UseElementVisibility>
        </div>
        <div class="not-prose mt-12">
            <el-button type="danger" size="large" tag="router-link" to="/">
                <template #icon>
                    <Icon icon="fa-solid:angle-double-left"></Icon>
                </template>
                {{ t(1010) }}
            </el-button>
        </div>
    </div>
</template>

<script setup lang="js">
import { inject, reactive } from "vue";
import { useI18n } from "vue-i18n";
import { UseElementVisibility } from "@vueuse/components";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    slide = reactive({}),
    { t, tm } = useI18n({
        messages: {
            en: {
                0: "We organize top-tier medical care",
                1: "Our workflow: You arrive at the \"{t2}\" office at a time convenient for you. Our specialist carefully reviews your situation, existing medical records, medical history, selects the best and most suitable practicing doctors for diagnosis and treatment, and quickly arranges appointments with physicians.",
                2: "Vsya Meditsina",
                3: "Then meets you at the medical facility, promptly guides you through all necessary departments without waiting in queues, if needed organizes hospitalization with comfortable accommodations, and personally oversees every stage of medical care throughout our cooperation.",
                4: "All our specialists have higher medical education and extensive clinical and administrative experience.",
                5: "List of clinics we work with",
                list1: [
                    {
                        to: "http://www.gvkg.ru/",
                        title: "Main Military Clinical Hospital named after N.N. Burdenko",
                        description: "The hospital has a history of over 300 years. Today, it is one of the largest multidisciplinary medical centers in Russia and a flagship of domestic military medicine. The hospital carefully preserves the heroic traditions of previous generations of military doctors and maintains a high scientific and professional level. Specialized diagnostic and treatment centers are established within the hospital, focused on the most relevant medical specialties."
                    },
                    {
                        to: "https://botkinmoscow.ru/",
                        title: "City Clinical Hospital named after S.P. Botkin",
                        description: "One of the oldest clinics in the city. Today, S.P. Botkin City Clinical Hospital is a modern multidisciplinary facility offering all types of treatment. Over 70 departments serve patients. From 2013 to 2017, as part of Moscow healthcare modernization, more than 8,000 units of modern medical equipment were purchased for over 3 billion rubles. Over 100 hospital doctors completed internships at leading foreign clinics."
                    },
                    {
                        to: "http://gkb1.ru/",
                        title: "First City Hospital named after N.I. Pirogov",
                        description: "One of Russia's leading multidisciplinary hospitals. For over two centuries, the institution has provided medical care to those in need. Today, the hospital operates using the latest technologies in line with the highest international standards and is equipped with modern diagnostic equipment."
                    },
                    {
                        to: "https://gkbe.ru/",
                        title: "City Clinical Hospital No. 20 (A.K. Yeramishantsev Hospital)",
                        description: "Most departments are specialized, including the country's only department for abdominal surgery and acute biliary tract pathology, where the first liver transplant in Russia was performed by Professor Yeramishantsev. The hospital houses the only department in Russia treating patients in crisis and borderline conditions with suicidal tendencies. The maternity ward is the only one in Moscow for pregnant women with kidney disease."
                    },
                    {
                        to: "http://www.gnck.ru/",
                        title: "National Medical Research Center of Coloproctology named after A.N. Ryazhikh",
                        description: "One of Russia's most authoritative specialized research and clinical institutions, and the only one entirely dedicated to the diagnosis and treatment of intestinal, rectal, pelvic and perineal diseases. Specialists at the Center successfully solve complex medical challenges in general and reconstructive coloproctology, endoscopy, oncology, functional and radiological diagnostics, surgery, and gastroenterology."
                    },
                    {
                        to: "https://filatovmos.ru/",
                        title: "N.F. Filatov City Children's Clinical Hospital No. 13",
                        description: "\"Filatov Hospital\" is a legendary institution traditionally recognized as a leader in Russian medicine for pediatric care. Today, the hospital is a modern multidisciplinary medical facility comprising an inpatient ward, day hospital, Ambulatory Surgery Center, City Consultative-Diagnostic Center, polyclinic, and emergency trauma care unit."
                    },
                    {
                        to: "https://dgkbsv.mos.ru/",
                        title: "City Children's Clinical Hospital of Saint Vladimir",
                        description: "One of Moscow's largest pediatric medical institutions. Built and opened its doors to the first patients in the summer of 1876. In 1922, it was renamed Rusakov Hospital. In the 1990s, the hospital regained its historical name. The hospital is equipped with all necessary diagnostic equipment, including CT scanners, ultrasound and endoscopic devices."
                    },
                    {
                        to: "https://www.nsi.ru/",
                        title: "Burdenko National Medical Research Center of Neurosurgery",
                        description: "The leading neurosurgical institution of the Russian Federation and one of the world’s foremost neurosurgical clinics, with a rich history, state-of-the-art equipment, and a unique professional team. The structure of the Institute allows for examination and treatment of patients with virtually any disorders of the central and peripheral nervous systems."
                    },
                    {
                        to: "https://www.vishnevskogo.ru/",
                        title: "Vishnevskiy Institute of Surgery",
                        description: "One of Russia’s leading medical institutions. Patients and doctors turn here in the most difficult cases requiring consultation or surgical intervention of the highest complexity, involving specialists from various fields. As recognized experts in different areas of surgery, key staff members are invited to develop national clinical guidelines for surgical disease treatment."
                    },
                    {
                        to: "https://sechenovclinic.ru/",
                        title: "V.F. Snegirev Obstetrics and Gynecology Clinic",
                        description: "Since its foundation, the clinic has shaped the national school of highly qualified obstetricians and gynecologists, laying the foundation for Russian science and practice in childbirth and treatment of obstetric and gynecological pathologies. Key features of the clinic’s activities include well-organized obstetric and gynecological care, consistently friendly attitude toward patients, gentle childbirth, prevention of possible complications, and management of delivery with minimal risk to mother, fetus, and newborn."
                    },
                    {
                        to: "https://neuromedic.ru/",
                        title: "A.Ya. Kozhevnikov Clinic of Nervous Diseases",
                        description: "The largest neurological clinic in Russia. The clinic houses neurological and neurosurgical departments. It includes a radiological diagnostics department, a functional diagnostics department in neurophysiology, and a clinical diagnostic laboratory, enabling all necessary examinations for neurological patients. The clinic hosts the Department of Nervous Diseases, training students, interns, residents, graduate students, and doctoral candidates in neurology, as well as scientific laboratories."
                    },
                    {
                        to: "https://www.tareevclinic.ru/",
                        title: "E.M. Tareev Clinic of Rheumatology, Nephrology and Occupational Pathology",
                        description: "One of the country’s leading medical institutions. From 1986 to 2018, the clinic was headed by Academician N.A. Mukhin. It is part of the Sechenov University University Clinical Hospital No. 3. It serves as the base for the Department of Internal, Occupational Diseases and Rheumatology at Sechenov University and the Department of Internal Diseases at Lomonosov Moscow State University. Treatment of kidney diseases, rheumatoid arthritis, systemic vasculitis and other rheumatic diseases, liver, gastrointestinal and lung diseases, and various rare conditions. Diagnosis of complex cases."
                    },
                    {
                        to: "http://www.med-rf.ru/",
                        title: "Medical Rehabilitation Center of the Ministry of Health of Russia",
                        description: "One of the first Russian medical institutions to apply European healthcare standards: early diagnosis, timely treatment, and rehabilitation after illness or surgery of any complexity to improve quality of life. Equipped with the best diagnostic tools, modern treatment technologies, and emergency surgical care, staffed by specialists in leading medical fields whose achievements are recognized by the Russian and global medical communities."
                    },
                    {
                        to: "http://mntk.ru/",
                        title: "MNTK Microsurgery of the Eye named after Academician S.N. Fyodorov",
                        description: "The main goal of MNTK is the development and rapid implementation in medical practice of advanced methods for diagnosing and treating eye diseases, creating the necessary technologies, while also addressing the important social task of making these achievements accessible to residents across all regions of Russia."
                    },
                    {
                        to: "http://мороздгкб.рф/",
                        title: "Morozovskaya City Children's Clinical Hospital of the Moscow Department of Health",
                        description: "One of the most renowned children's hospitals in Russia and Europe. Located on nine hectares in the historic center of the capital, it resembles a small town in spirit. At Morozovskaya Hospital, 13 unique Centers for specialized pediatric medical care have been established and continuously operate. The hospital is equipped with over 3,000 units of unique and state-of-the-art medical equipment. A team of specialist doctors works around the clock without days off, providing emergency multidisciplinary medical care."
                    },
                    {
                        to: "https://niigb.ru/",
                        title: "Research Institute of Eye Diseases",
                        description: "Russia’s largest ophthalmological center, providing all types of diagnostics and treatment for eye diseases, as well as conducting scientific research on the most pressing issues in ophthalmology. The institute’s scientific and educational activities include fundamental biomedical research, development of new diagnostic, treatment, and prevention methods for various eye diseases, training of scientific personnel, and education and professional development of ophthalmologists."
                    },
                    {
                        to: "https://sklif.mos.ru/",
                        title: "N.V. Sklifosovsky Research Institute of Emergency Care",
                        description: "Currently, the N.V. Sklifosovsky Institute of Emergency Care is the largest multidisciplinary scientific and practical center for emergency medical care, resuscitation, urgent surgery, combined and burn injuries, acute poisoning, and emergency cardiology. The institute has over 40 scientific divisions, more than half of which are clinical, corresponding to the most common emergency pathologies."
                    },
                    {
                        to: "https://www.neurology.ru/",
                        title: "Scientific Center of Neurology",
                        description: "Throughout its history, the Institute has been the leading scientific, clinical-diagnostic, and educational center in neurology in Russia and a WHO Regional Neuroscience Center. With a state-of-the-art research and diagnostic base comparable to the largest foreign centers of similar profile, the Institute focuses on creating cutting-edge medical technologies for the diagnosis, treatment, and prevention of the most common and socially significant nervous system diseases—stroke and its consequences, vascular dementia, Parkinson’s disease, multiple sclerosis, polyneuropathies, critical neurological conditions, hereditary nervous system diseases, and others."
                    },
                    {
                        to: "https://bakulev.ru/",
                        title: "A.N. Bakulev National Medical Research Center of Cardiovascular Surgery",
                        description: "One of the largest scientific centers in the world in cardiovascular surgery and cardiology, and the leading institution in Russia in the field of \"cardiovascular surgery.\" The Center’s clinical activities focus on providing surgical care to patients of all ages, from the first day of life, for any cardiovascular pathologies. It holds leading positions in Europe in the number of open-heart surgeries performed using cardiopulmonary bypass."
                    },
                    {
                        to: "https://www.ckb2rzd.ru/",
                        title: "No. 2 Clinical Hospital named after N.A. Semashko of JSC Russian Railways",
                        description: "The clinic is equipped with modern treatment and diagnostic equipment. Modern diagnostic methods (MRI, CT) and combined treatment methods are used, including minimally invasive surgical procedures and video-laparoscopic operations. Since the hospital's founding, specialists have performed over one million surgeries."
                    },
                    {
                        to: "https://sechenovclinic.ru/hospitals/list.php?sid=114",
                        title: "First Sechenov University Clinical Hospital No. 1",
                        description: "Preserving the best traditions of domestic medicine, the hospital continuously improves its treatment processes. A wide range of diagnostic services is provided at Clinical Hospital No. 1. Patients have access to modern specialized medical care, comfortable accommodations, and individualized attention, allowing it to remain among the leaders in Russian healthcare."
                    },
                    {
                        to: "https://cardioweb.ru/",
                        title: "National Medical Research Center of Cardiology of the Ministry of Health of Russia",
                        description: "The leading research, medical, and educational institution in Russia—the first domestic realization of the concept of translational medicine, an interdisciplinary field integrating clinical medicine, molecular and cellular biology, medical biochemistry, genetics, human physiology, and biotechnological approaches to the development, production, and implementation of new therapeutic and diagnostic tools, as well as innovative surgical techniques."
                    },
                    {
                        to: "https://med.ru/",
                        title: "B.V. Petrovsky Russian Scientific Center of Surgery",
                        description: "The largest multidisciplinary surgical research institution, whose specialists conduct diagnostics, treatment, and rehabilitation of patients after unique operations at a modern global level. The center comprises three buildings: cardiothoracic surgery, a scientific treatment and diagnostic center, and a diagnostic research center."
                    },
                    {
                        to: "https://www.ronc.ru/",
                        title: "N.N. Blokhin National Medical Research Center of Oncology",
                        description: "An independent medical and scientific organization with the status of a state institution, one of the largest oncology clinics in the world, equipped with the latest technology and all advanced methods of cancer diagnosis and treatment. It provides high-tech oncological care at the level of the best global standards, using many innovative, including unique, technologies to save patients. Eight departments of medical academies and universities operate at the center."
                    },
                    {
                        to: "https://volynka.ru/",
                        title: "Federal Clinical Hospital No. 1 (Volynskaya) of the Presidential Executive Office of the Russian Federation",
                        description: "The best traditions of Kremlin medicine, the most modern, new, and prestigious healthcare technologies; one of the few hospitals in Russia meeting global standards for multidisciplinary inpatient care; experience in treating prominent government officials, world-renowned scientists, and distinguished cultural and artistic figures; highly qualified specialists: professors, doctors and candidates of sciences, physicians of the highest category; 24/7 operation of all clinical departments."
                    },
                    {
                        to: "https://fmbafmbc.ru/",
                        title: "A.I. Burnazyan Federal Medical and Biophysical Center",
                        description: "A powerful scientific and clinical cluster within the Federal Medical and Biological Agency. The FMBC is the flagship institution of Russian healthcare in biophysics, radiation and nuclear medicine and safety, surgery and transplantation, neurosurgery, hematology, oncology, urology and andrology, neurology and neurorehabilitation, resuscitation, as well as modern disease diagnostics and innovative biomedical technologies."
                    },
                    {
                        to: "https://www.celt.ru/",
                        title: "Center for Endosurgery and Lithotripsy",
                        description: "A truly multidisciplinary clinic offering a wide range of services, where both adults and children can receive care in more than 50 medical specialties. The center has been actively operating in the private healthcare market since 1993. No other multidisciplinary private clinic in Russia has comparable experience. The CELT has extensive diagnostic capabilities. The clinic offers comfortable single, double, and two-room rooms. Patients have access to a guarded parking lot available 24/7."
                    },
                    {
                        to: "https://ckb-rzd.ru/",
                        title: "Central Clinical Hospital No. 1 of RZD-Medicine",
                        description: "A large multidisciplinary hospital with over 80 years of history. The clinic perfectly combines the best traditions of institutional medicine, excellent staffing, and modern equipment. The clinic has brought together top specialists, doctors and candidates of medical sciences, clinicians, and physicians of the highest category, and most importantly, established a system of interaction that allows a comprehensive approach to solving patient problems and offering the most correct and safe treatment path."
                    },
                    {
                        to: "https://www.cito-priorov.ru/",
                        title: "N.N. Priorov National Medical Research Center of Traumatology and Orthopedics",
                        description: "A first-category institute and a multidisciplinary research institution where leading specialists in traumatology, orthopedics, bone pathology, and prosthetics work, widely known in Russia and abroad. The Center hosts a training department for traumatologists-orthopedists (RMANPO). The Center has a scientific and technical department with a laboratory for testing new materials and medical equipment and metrology."
                    },
                    {
                        to: "https://www.cniis.ru/",
                        title: "Central Research Institute of Dentistry and Maxillofacial Surgery",
                        description: "The leading institution in the country for dentistry and maxillofacial surgery. Since its establishment in 1962, the Central Research Institute of Dentistry and Maxillofacial Surgery (CNIIS) has coordinated scientific activities in dentistry across research, educational, and medical institutions in the country. Dentistry and a unique school of cranio-maxillofacial surgery have developed side by side at the institute. Today, the institute’s specialists actively participate in the implementation of the national project \"Health\" in the area of high-tech medical care. CNIIS is an excellent training ground for medical professionals, where dentists and maxillofacial surgeons from Russia and abroad regularly upgrade their qualifications."
                    }
                ],
                1010: "back to home page"
            },
            ru: {
                0: "Организуем медицинское обслуживание по высшему разряду",
                1: "Алгоротим взаимодействия – Вы приезжаете в офис компании \"{t2}\" в удобное для Вас время. Наш специалист внимательно изучает Вашу ситуацию, имеющуюся медицинскую документацию, анамнез и подбирает лучших, наиболее подходящих практикующих докторов, для проведения диагностики и лечения, максимально быстро организует встречи с врачами.",
                2: "Вся медициина",
                3: "Затем встречает Вас в лечебном учреждении, оперативно, без очередей проводит Вас по всем кабинетам, при необходимости организует госпитализацию с предоставлением комфортных условий пребывания, лично контролирует каждый этап медицинской помощи на всём протяжении нашего сотрудничества.",
                4: "Все специалисты нашей компании имеют высшее медицинское образование и опыт работы как клинический, так и административный.",
                5: "Список клиник, с которыми мы сотрудничаем",
                list1: [
                    {
                        to: "http://www.gvkg.ru/",
                        title: "Главный военный клинический госпиталь имени Н.Н Бурденко",
                        description: "Госпиталь имеет более чем 300-летнюю историю. Сегодня это один из крупнейших многопрофильных лечебных центров России, флагман отечественной военной медицины. В стенах госпиталя бережно хранятся героические традиции предшествующих поколений военных врачей, сохраняется высокий научный и профессиональный потенциал. В госпитале развернуты специализированные лечебно-диагностические центры, профилированные по наиболее актуальным медицинским специальностям."
                    },
                    {
                        to: "https://botkinmoscow.ru/",
                        title: "Городская клиническая больница имени С.П.Боткина",
                        description: "Одна из старейших клиник в городе. Сегодня ГБУЗ ГКБ им. С.П.Боткина - современный многопрофильный стационар, где можно получить все виды лечения. Пациентов принимают более 70 отделений. С 2013 года по 2017 годы в рамках программы модернизации московского здравоохранения было закуплено более 8 тысяч единиц современной медицинской техники на сумму более 3 миллиардов рублей. Более 100 врачей больницы прошли стажировки в ведущих зарубежных клиниках."
                    },
                    {
                        to: "http://gkb1.ru/",
                        title: "Первая Градская больница имени Н.И.Пирогова",
                        description: "Одна из ведущих многопрофильных больниц России. Вот уже более двух веков учреждение оказывает медицинскую помощь нуждающимся. Сегодня больница работает с применением новейших технологий в соответствии с самыми высокими мировыми стандартами, оснащена современным диагностическим оборудованием."
                    },
                    {
                        to: "https://gkbe.ru/",
                        title: "Городская клиническая больница №20 (ГКБ имени А.К.Ерамишанцева)",
                        description: "Большая часть отделений является специализированными, в том числе единственное в стране отделение абдоминальной хирургии и острой патологии желчно-выводящих путей, первая в стране пересадка печени произведена на базе этого отделения профессором Ерамишанцевым. Единственное в стране отделение, занимающееся пациентами в кризисных, пограничных состояниях с покушениями на суицид. Родильное отделение единственное в Москве для беременных с почечной патологией."
                    },
                    {
                        to: "http://www.gnck.ru/",
                        title: "Национальный медицинский исследовательский центр колопроктологии имени А.Н.Рыжих",
                        description: "Одно из авторитетнейших специализированных научно-клинических учреждений России, и единственное — целиком специализирующееся на диагностике и лечении заболеваний кишечника, заднего прохода, органов таза и промежности. Специалисты Центра с успехом решают сложнейшие медицинские задачи в сфере общей и реконструктивной колопроктологии, эндоскопии, онкологии, функциональной и лучевой диагностики, хирургии, гастроэнтерологии."
                    },
                    {
                        to: "https://filatovmos.ru/",
                        title: "Детская городская клиническая больница №13 имени Н.Ф.Филатова",
                        description: "\"Филатовская больница\" – легендарное учреждение, традиционно являющееся лидером отечественной медицины в области медицинской помощи детям. Сейчас больница – современное многопрофильное лечебное учреждение, в состав которого входит стационар, стационар дневного пребывания, Центр амбулаторной хирургии, Городской консультативно-диагностический центр, поликлиника и пункт неотложной травматологической помощи."
                    },
                    {
                        to: "https://dgkbsv.mos.ru/",
                        title: "Детская городская клиническая больница святого Владимира",
                        description: "Больница является одним из крупнейших детских лечебных учреждений Москвы. Была построена и приняла первых пациентов летом 1876 года. В 1922 году была переименована в больницу имени Русакова. И в 1990-х годах больнице было возвращено ее историческое название. Больница оснащена всем необходимым диагностическим оборудованием, включая компьютерную томографию, ультразвуковую и эндоскопическую аппаратуру."
                    },
                    {
                        to: "https://www.nsi.ru/",
                        title: "ФГАУ НМИЦ нейрохирургии имени академика Н.Н.Бурденко",
                        description: "Головное нейрохирургическое учреждение Российской Федерации, ведущая нейрохирургическая клиника мира с богатой историей, самым современным оснащением и уникальным профессиональным коллективом. Структура Института нейрохирургии позволяет проводить обследование и лечение больных практически с любыми заболеваниями центральной и периферической нервной системы."
                    },
                    {
                        to: "https://www.vishnevskogo.ru/",
                        title: "Институт хирургии имени А.В.Вишневского",
                        description: "Одно из ведущих медицинских учреждений России. Именно сюда и пациенты, и врачи обращаются в самых непростых ситуациях, когда требуется консультация или хирургическая помощь высочайшей степени сложности, с участием специалистов разного профиля. Как признанные эксперты в разных областях хирургии, ключевые сотрудники Центра приглашены к разработке национальных клинических рекомендаций по лечению хирургических заболеваний."
                    },
                    {
                        to: "https://sechenovclinic.ru/",
                        title: "Клиника акушерства и гинекологии имени В.Ф.Снегирева",
                        description: "Со дня основания в клинике формировалась отечественная школа из высококвалифицированных акушеров-гинекологов, которая заложила основы Российской науки и практики родовспоможения и лечения акушерско-гинекологической патологии. Основными особенностями деятельности клиники являются: хорошая организация акушерско-гинекологической помощи, неизменно доброжелательное отношение к пациенткам, бережное родоразрешение, предупреждение возможных осложнений, ведение родов с наименьшим риском для матери, плода и новорожденного."
                    },
                    {
                        to: "https://neuromedic.ru/",
                        title: "Клиника нервных болезней имени А.Я.Кожевникова",
                        description: "Является крупнейшей неврологической клиникой России. В клинике находятся неврологические и нейрохирургическое отделения. На базе клиники базируются отделение лучевой диагностики, отделение функциональной диагностики по нейрофизиологии, клинико-диагностическая лаборатория, что позволяет проводить все необходимые исследования неврологическим пациентам. На базе клиники работает кафедра нервных болезней, осуществляющая подготовку студентов, интернов, ординаторов, аспирантов, докторантов по неврологии, а также научные лаборатории."
                    },
                    {
                        to: "https://www.tareevclinic.ru/",
                        title: "Клиника ревматологии, нефрологии и профпатологии имени Е.М.Тареева",
                        description: "Одно из ведущих лечебных учреждений страны. С 1986 по 2018 гг клиникой руководил академик Н.А.Мухин. Входит в состав Университетской клинической больницы №3 Сеченовского университета. Является базой кафедры внутренних, профессиональных болезней и ревматологии Сеченовского университета и кафедры внутренних болезней МГУ им. М.В.Ломоносова. Лечение заболеваний почек, ревматоидного артрита, системных васкулитов и других ревматических болезней, заболеваний печени, желудочно-кишечного тракта, легких, различных редких заболеваний. Диагностика сложных случаев."
                    },
                    {
                        to: "http://www.med-rf.ru/",
                        title: "Лечебно-реабилитационный центр Минздрава России",
                        description: "Одно из первых российских медицинских учреждений, в котором применяются стандарты европейской системы медицинского обслуживания – ранняя диагностика, своевременное лечение и реабилитацияпосле перенесенной болезни или операции любой степени сложности для повышения качества жизни. Лучшее диагностическое оборудование, современные лечебные технологии и экстренная оперативная помощь, специалисты ведущих направлений медицины, чьи достижения признаны российским и мировым медицинским сообществом."
                    },
                    {
                        to: "http://mntk.ru/",
                        title: "МНТК Микрохирургия глаза имени академика С.Н.Федорова",
                        description: "Основная цель МНТК - разработка и быстрое внедрение в медицинскую практику передовых методов диагностики и лечения глазных заболеваний, создание необходимых для этого технологий и в то же время решение важной социальной задачи - сделать эти достижения доступными для жителей всех регионов России."
                    },
                    {
                        to: "http://мороздгкб.рф/",
                        title: "Морозовская детская городская клиническая больница Департамента здравоохранения города Москвы",
                        description: "Одна из самых известных в России и Европе детская больница. Расположенная на девяти гектарах в историческом центре столицы по своему духу она напоминает маленький город. На базе Морозовской больницы сформированы и постоянно функционируют 13 уникальных Центров городской специализированной медицинской помощи для детей и подростков. В Морозовской больнице установлено более 3 тысяч единиц уникального и новейшего медицинского оборудования. В больнице без выходных в круглосуточном режиме работает бригада врачей-специалистов, позволяющая оказывать экстренную многопрофильную медицинскую помощь."
                    },
                    {
                        to: "https://niigb.ru/",
                        title: "ФГБНУ Научно-исследовательский институт глазных болезней",
                        description: "Крупнейший в России офтальмологический центр, где проводятся все виды диагностики и лечения глазных заболеваний, а также ведется научная работа по наиболее актуальным проблемам офтальмологии. Научно-образовательная деятельность института заключается в фундаментальных биомедицинских исследованиях, разработке новых методов диагностики, лечения и профилактики различных глазных заболеваний, подготовке научных кадров, обучении и повышении квалификации врачей-офтальмологов."
                    },
                    {
                        to: "https://sklif.mos.ru/",
                        title: "НИИ скорой помощи имени Н.В.Склифосовского",
                        description: "В настоящее время институт скорой помощи имени Н.В.Склифосовского является крупнейшим многопрофильным научно-практическим центром по оказанию скорой медицинской помощи, реанимации, неотложной хирургии, сочетанной и ожоговой травмы, острых отравлений и неотложной кардиологии. Всего в институте сформировано более 40 научных подразделений, и более половины из них — клинические, которые соответствуют профилю наиболее распространенных неотложных патологий."
                    },
                    {
                        to: "https://www.neurology.ru/",
                        title: "Научный центр неврологии",
                        description: "На протяжении всей своей истории Институт являлся ведущим научным, лечебно-диагностическим и учебным центром страны в области неврологии, региональным Центром ВОЗ по нейронаукам. Обладая самой современной исследовательской и диагностической базой, не уступающей крупнейшим зарубежным центрам аналогичного профиля, Институт основное внимание уделяет созданию новейших медицинских технологий диагностики, лечения и профилактики наиболее распространенных и социально значимых заболеваний нервной системы — инсульта и его последствий, сосудистой деменции, болезни Паркинсона, рассеянного склероза, полиневропатий, критических состояний в неврологии, наследственных болезней нервной системы и др."
                    },
                    {
                        to: "https://bakulev.ru/",
                        title: "Национальный медицинский исследовательский центр сердечно-сосудистой хирургии имени А.Н.Бакулева",
                        description: "Один из крупнейших в мире научных центров в области кардиохирургии и кардиологии, головное учреждение Российской Федерации по профилю \"сердечно- сосудистая хирургия\". Клиническая деятельность Центра направлена на оказание хирургической помощи пациентам всех возрастов, начиная с первого дня жизни, при любых патологиях сердечно-сосудистой системы. Занимает лидирующие позиции в Европе по количеству проведенных операций на \"открытом\" сердце с применением искусственного кровообращения."
                    },
                    {
                        to: "https://www.ckb2rzd.ru/",
                        title: "ЦКБ №2 имени Н.А.Семашко ОАО РЖД",
                        description: "Клиника располагает современным лечебным и диагностическим оборудованием. Используются современные методы диагностики (МРТ, КТ), а также комбинированные методы лечения, в том числе малоинвазивные хирургические вмешательства и видео-лапароскопические операции. С момента основания больницы специалистами выполнено более 1 миллиона операций."
                    },
                    {
                        to: "https://sechenovclinic.ru/hospitals/list.php?sid=114",
                        title: "Первый МГМУ имени И.М.Сеченова Университетская клиническая больница №1",
                        description: "Сохраняя лучшие традиции отечественной медицины, больница непрерывно совершенствует лечебный процесс. В УКБ №1 оказывается широкий спектр диагностических услуг. Имеется возможность получения современной специализированной медицинской помощи, комфортные условия пребывания и индивидуальный подход к каждому пациенту, что позволяет быть в числе лидеров отечественного здравоохранения."
                    },
                    {
                        to: "https://cardioweb.ru/",
                        title: "ФГБУ НМИЦ кардиологии Минздрава России",
                        description: "Является ведущим в России научно-исследовательским, медицинским и образовательным учреждением – первой отечественной реализацией концепции трансляционной медицины, как междисциплинарной области знаний, интегрирующей элементы клинической медицины, молекулярной и клеточной биологии, медицинской биохимии, генетики и физиологии человека, а также биотехнологических подходов к разработке, производству и внедрению в практику новых терапевтических и диагностических средств, а также инновационных хирургических методик."
                    },
                    {
                        to: "https://med.ru/",
                        title: "Российский научный центр хирургии имени академика Б.В.Петровского",
                        description: "Крупнейшее многопрофильное хирургическое научно-исследовательское учреждение, специалисты которого на современном мировом уровне проводят диагностику заболеваний, лечение и реабилитацию пациентов после уникальных операций. Располагает тремя корпусами – кардиохирургии, научного лечебно-диагностического центра и диагностических исследований."
                    },
                    {
                        to: "https://www.ronc.ru/",
                        title: "НМИЦ онкологии имени Н.Н.Блохина",
                        description: "Является самостоятельной медицинской научной организацией, имеющей статус государственного учреждения, одна из самых крупных онкологических клиник в мире, имеющая в своем арсенале новейшее оборудование и все передовые методики диагностики и лечения рака. Оказывает высокотехнологичную онкологическую помощь на уровне лучших мировых стандартов, применяя для спасения пациентов многие инновационные, в том числе уникальные технологии. На базе центра работают 8 кафедр медицинских академий и университетов."
                    },
                    {
                        to: "https://volynka.ru/",
                        title: "ФГБУ Клиническая больница №1 (Волынская) Управления делами Президента РФ",
                        description: "Лучшие традиции кремлевской медицины, самые современные, новые и престижные технологии в здравоохранении; одна из немногих больниц России, соответствующих мировым стандартам, предъявляемым к многопрофильным стационарам; опыт в лечении видных государственных деятелей, ученых с мировым именем, заслуженных деятелей культуры и искусства; высококвалифицированные специалисты: профессора, доктора и кандидаты наук, врачи высшей категории; круглосуточная работа всех клинических отделений больницы."
                    },
                    {
                        to: "https://fmbafmbc.ru/",
                        title: "Федеральный медицинский биофизический центр имени А.И.Бурназяна",
                        description: "Мощный научно-клинический кластер в системе Федерального медико-биологического агентства. ФМБЦ является флагманским учреждением российского здравоохранения в области биофизики, радиационной и ядерной медицины и безопасности, хирургии и трансплантологии, нейрохирургии, гематологии, онкологии, урологии и андрологии, неврологии и нейрореабилитации, реаниматологии, а также современной диагностики заболеваний и инновационных биомедицинских технологий."
                    },
                    {
                        to: "https://www.celt.ru/",
                        title: "Центр Эндохирургии и Литотрипсии",
                        description: "По настоящему многопрофильная клиника с огромным спектром услуг, в которой и взрослые и дети могут получить помощь более чем по 50 медицинским специальностям. Активно работает на рынке платных медицинских услуг с 1993 года. Подобного опыта успешной деятельности нет практически ни у одной многопрофильной частной клиники России. ЦЭЛТ обладает широким спектром диагностических возможностей. Клиника располагает комфортабельными одно, двухместными, а также двухкомнатными палатами. В распоряжении пациентов есть автостоянка с круглосуточной охраной."
                    },
                    {
                        to: "https://ckb-rzd.ru/",
                        title: "ЧУЗ Центральная клиническая больница №1 РЖД-Медицина",
                        description: "Крупная многопрофильная больница более чем с 80-летней историей. В клинике идеально совмещены лучшие традиции ведомственной медицины, великолепный кадровый потенциал и современное оборудование.В стенах клиники удалось собрать высококлассных специалистов, докторов и кандидатов медицинских наук, клиницистов, врачей высшей категории, а самое важное — построить систему взаимодействия, при которой можно комплексно подходить к решению проблем пациентов и предлагать наиболее правильный и безопасный путь лечения."
                    },
                    {
                        to: "https://www.cito-priorov.ru/",
                        title: "Национальный медицинский исследовательский центр травматологии и ортопедии имени Н.Н.Приорова",
                        description: "Институт первой категории, многопрофильное научно-исследовательское учреждение, в котором работают ведущие специалисты в области травматологии, ортопедии, костной патологии и протезирования, широко известен в нашей стране и за рубежом. На базе Центра работает кафедра повышения квалификации травматологов-ортопедов (РМАНПО). Центр имеет научно-технический отдел с лабораторией испытания новых материалов медицинской техники и метрологии."
                    },
                    {
                        to: "https://www.cniis.ru/",
                        title: "Центральный научно-исследовательский институт стоматологии и челюстно-лицевой хирургии",
                        description: "Является головным учреждением страны по проблемам стоматологии и челюстно-лицевой хирургии. С момента своего создания в 1962 году ЦНИИС координирует научную деятельность по вопросам стоматологии, проводимую в научных, учебных и лечебных учреждениях страны. В институте стоматология развивается бок о бок с уникальной школой черепно-челюстно-лицевой хирургии. Сегодня специалисты института активно участвуют в реализации национального проекта \"Здоровье\" в области оказания высокотехнологичной медицинской помощи. ЦНИИС - прекрасная кузница врачебных кадров, здесь регулярно проходят повышение квалификации врачи-стоматологи и челюстно-лицевые хирурги России, стран ближнего и дальнего зарубежья."
                    },
                ],
                1010: "на главную",
            }
        }
    });

__unocss_runtime.extract("bg-white/85");

</script>