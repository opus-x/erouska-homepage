<template>
    <div>
        <section class="heading" id="uvod">
            <h1 class="heading__title">Časté dotazy</h1>
        </section>  <!-- /heading -->

        <main class="main" role="main">
            <section class="section" v-for="section in sections" :id="section.section_anchor">
                <h2 :class="'section__title section__title--' + section.color">{{ $t('web.faq.sections.' + section.section_id) }}</h2>
                <div class="section__content">
                    <div class="faq">
                        <div v-for="(question, q_index) in section.questions" :id="question.anchor"
                        :class="[q_index == 0 ? 'faq__item--open' : '', 'section__item faq__item']">
                            <h3 class="faq__q">{{ $t('web.faq.questions.' + question.id + '.question') }}</h3>
                            <div class="faq__a">
                                <template v-for="(item, index) in Object.keys($i18n.messages[$i18n.fallbackLocale].web.faq.questions[question.id].answer).length">
                                   <div v-if="['<ul>', '<ol>', '<h4>'].some(v => $t('web.faq.questions.' + question.id + '.answer[' + index + ']').substring(0, 4).includes(v))"
                                   v-html="$t('web.faq.questions.' + question.id + '.answer[' + index + ']')"></div>
                                   <p v-else v-html="$t('web.faq.questions.' + question.id + '.answer[' + index + ']')"></p>
                                </template>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <box/>
        </main>
    </div>
</template>

<script>
    import Box from '~/components/Box.vue'
    import sectionsJson from '~/assets/faq.json'

    export default {
        data() {
            return {
                sections: sectionsJson
            }
        },
        components: {
            Box
        },
        head() {
            return {
                title: this.$t('web.faq.page_title'),
                bodyAttrs: {
                    class: 'page-single page-caste-dotazy'
                }
            }
        }
    }
</script>
