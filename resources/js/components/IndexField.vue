<template>
    <div>
      <img :src="domain + fieldValue" style="height: 50px" alt="">
    </div>
</template>

<script>
export default {
    props: ['resourceName', 'field'],

    data() {
        return {
            domain: null
        }
    },

    async mounted() {
      this.getFullDomainWithProtocol()
    },

    methods: {
        getFullDomainWithProtocol() {
            const protocol = window.location.protocol;
            const hostname = window.location.hostname;
            const port = window.location.port ? ':' + window.location.port : '';

            this.domain = `${protocol}//${hostname}${port}`;
        },
    },

    computed: {

        fieldValue() {
            return this.field.displayedAs || this.field.value
        },
    }
}
</script>
