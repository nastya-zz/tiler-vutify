<template>
    <v-responsive :class="styles">
        <section :id="id">
            <div class="py-12"></div>
            <v-container  class="text-center">
                <h2 class="text-sm-h3 text-md-h2 text-xl-h1 mb-3">{{title}}</h2>
                <v-responsive class="mx-auto mb-8" style="width: 56px">
                    <v-divider :class="'mb-2 ' + dark" ></v-divider>
                    <v-divider :class="dark"></v-divider>
                </v-responsive>
                <slot></slot>
            </v-container>
        </section>
    </v-responsive>
</template>

<script>
	export default {
		name: "Section",
        props: {
			title: String,
            id: String,
            styles: String,
            dark: String
        }
	}
</script>

<style scoped>

</style>
