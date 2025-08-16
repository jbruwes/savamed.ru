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
    <div class="container mx-auto my-48" un-cloak>

        <h2>НАШ АДРЕС:</h2>
        <p>Москва<br>Старокирочный переулок д. 6</p>
        <h2>НАШИ ТЕЛЕФОНЫ:</h2>
        <p><a href="tel:+79151797755"
                style="font-family: Arsenal, sans-serif; text-decoration: none; color: #000000;">+7 (915) 179-77-55</a>
        </p>
        <p><a class="ui whatsapp button" href="https://wa.me/79151797755?text=Здравствуйте!%20Нужна%20помощь"
                rel="noopener" style="font-family: Arsenal, sans-serif;" target="_blank"><i class="whatsapp icon"></i>
                написать в WhatsApp </a></p>
        <h2>НАШ E-MAIL:</h2>
        <p><a href="mailto:info@savamed.ru">info@savamed.ru</a></p>
        <p><strong>Приём только по предварительной записи!</strong></p>
        <p>&nbsp;</p>
        <div class="ui segment">
            <div style="position: relative; height: 600px;"><iframe
                    style="border: 0; width: 100%; height: 600px; position: absolute; z-index: 0;" tabindex="0"
                    src="https://yandex.ru/map-widget/v1/-/CHhaf65c" frameborder="0" allowfullscreen="true"
                    aria-hidden="false"></iframe></div>
        </div>
        <p>&nbsp;</p>
        <p><a class="ui labeled icon red button" href="/" style="font-family: Arsenal, sans-serif;"><i
                    class="left arrow icon"></i>на главную</a></p>


    </div>
</template>

<script setup lang="js">
import { inject } from "vue";
import { useI18n } from "vue-i18n";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    { t } = useI18n({
        messages: {
            en: {
            },
            ru: {
            }
        }
    });
</script>