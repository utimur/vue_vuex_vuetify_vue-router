<template>
    <v-container>
        <v-row class="d-flex">
            <v-text-field v-model="title"/>
            <v-file-input v-model="img"/>
            <v-btn @click="addPhoto">Добавить</v-btn>
        </v-row>
    </v-container>
</template>

<script>
export default {
    data: () => ({
        title: '',
        img: null
    }),
    methods: {
        addPhoto() {
            const reader = new FileReader()
            reader.onload = () => {
                let photo = {
                    id: Date.now(),
                    title: this.title,
                    url: reader.result
                }
                this.$emit('addPhoto', photo)
            }
            reader.readAsDataURL(this.img)
        }
    }
}
</script>

<style scoped>

</style>
