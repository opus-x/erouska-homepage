<template>
    <div class="aside d-none d-xl-block">
        <h3 class="aside__title">{{ $t('web.faq.sections.table_of_contents') }}</h3>
        <ul class="aside__actions">
            <li v-for="(section, s_index) in sections">
                <a :href="'#' + section.section_anchor">
                    <b>{{ $t('web.faq.sections.' + section.section_id + '.title') }}</b>
                    <br>{{ $t('web.faq.sections.' + section.section_id + '.description') }}
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
    import sectionsJson from '~/assets/faq.json'

    export default {
        data() {
            return {
                sections: sectionsJson
            }
        }
    }
</script>
