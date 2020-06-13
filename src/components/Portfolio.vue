<template>
	<v-container fluid class="px-0 py-0 mx-0">
		<v-carousel
				cycle
				height="90vh"
				interval="5000"
				hide-delimiter-background
				show-arrows-on-hover
		>
			<v-carousel-item
					v-for="(slide, i) in slides"
					:key="i"
			>
				<v-sheet
						:color="colors[i]"
						height="100%"
				>
					<v-row
							class="fill-height"
							align="center"
							justify="center"
					>
						<div class="display-3">{{ slide }} Slide</div>
					</v-row>
				</v-sheet>
			</v-carousel-item>
		</v-carousel>

		<Section
        :title="'About us'"
        :id="'about-us'"
        :styles="'white'">
			<v-responsive
          style="max-width: 800px"
          class="mx-auto mb-8 text-md-body-1 text-xl-h5">
				<p class="px-4">
					Vuetify is the #1 component library for Vue.js and has been in active development since 2016. The goal of the
					project is to provide users with everything that is needed to build rich and engaging web applications using
					the Material Design specification. It accomplishes that with a consistent update cycle, Long-term Support
					(LTS) for previous versions, responsive community engagement, a vast ecosystem of resources and a dedication
					to quality components.
				</p>
			</v-responsive>
			<v-row class="py-2 flex-column flex-md-row align-center">
				<v-col
            cols="12"
            offset-md="2"
            md="4" sm="12"
            offset-sm="0"
            lg="3"
            offset-lg="3">
					<v-row class="flex-column">
						<v-col class="pb-sm-3">
							<v-avatar color="secondary darken-2 elevation-2" size="200">
								<span class="white--text headline">Vicktor</span>
							</v-avatar>
						</v-col>
						<v-col>
							<v-btn
                  href="#"
                  large
                  color="purple"
                  class="white--text">
								instagram
								<v-icon class="ml-2">fab fa-instagram</v-icon>
							</v-btn>
						</v-col>
					</v-row>
				</v-col>
				<v-col cols="12" sm="12" md="4" lg="3">
					<v-row class="flex-column">
						<v-col>
							<v-avatar color="secondary elevation-2 " size="200">
								<span class="white--text headline">Vitaliy</span>
							</v-avatar>
						</v-col>
						<v-col>
							<v-btn
                  href="#"
                  large
                  color="purple"
                  class="white--text">
								instagram
								<v-icon class="ml-2">fab fa-instagram</v-icon>
							</v-btn>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<div class="py-12"></div>
		</Section>

		<Section
        :title="'Features'"
        :id="'features'"
        :styles="'grey lighten-4'">
			<v-row class="flex-column flex-md-row align-center justify-center">
				<v-col md="4" sm="6">
					<v-card>
						<v-card-title class="mb-2">
							Top western road trips
							<v-icon class="ml-2" color="teal">fas fa-hand-holding-usd</v-icon>
						</v-card-title>

						<v-card-subtitle>
							Vuetify is the #1 component library for Vue.js and has been in active development since 2016.
						</v-card-subtitle>
						<v-img
								src="http://placehold.it/400x200"
								height="200px"
						></v-img>
					</v-card>
				</v-col>
				<v-col md="4" sm="6">
					<v-card>
						<v-card-title class="mb-2">
							Top western road trips
							<v-icon class="ml-2" color="teal">fas fa-shield-alt</v-icon>
						</v-card-title>

						<v-card-subtitle>
							Vuetify is the #1 component library for Vue.js and has been in active development since 2016.
						</v-card-subtitle>
						<v-img
								src="http://placehold.it/400x200"
								height="200px"
						></v-img>
					</v-card>
				</v-col>
				<v-col md="4" sm="6">
					<v-card>
						<v-card-title class="mb-2">
							Top western road trips
							<v-icon class="ml-2" color="teal">fas fa-user-clock</v-icon>
						</v-card-title>

						<v-card-subtitle>
							Vuetify is the #1 component library for Vue.js and has been in active development since 2016.
						</v-card-subtitle>
						<v-img
								src="http://placehold.it/400x200"
								height="200px"
						></v-img>
					</v-card>
				</v-col>
			</v-row>
			<div class="py-12"></div>
		</Section>

		<v-img
        :aspect-ratio="16/9"
        src="img/versace-tile.jpg"
        height="500"
        class="d-flex align-center">
			<v-row align="center" class="white--text pa-2">
				<v-col class="text-center">
					<div class="subheading">Jonathan Lee</div>
					<div class="body-1">heyfromjonathan@gmail.com</div>
				</v-col>
				<v-col class="text-center">
					<div class="subheading">Jonathan Lee</div>
					<div class="body-1">heyfromjonathan@gmail.com</div>
				</v-col>
				<v-col class="text-center">
					<div class="subheading">Jonathan Lee</div>
					<div class="body-1">heyfromjonathan@gmail.com</div>
				</v-col>
			</v-row>
		</v-img>

		<Section :title="'Blog'" :id="'blog'" :styles="'white'">
			<v-row>
				<v-col md="4" sm="6" v-for="(post, i) in posts" :key="i">
					<v-card>
						<v-img :src="post.img" height="300"></v-img>
						<v-card-subtitle>
							{{post.text}}
						</v-card-subtitle>
					</v-card>
				</v-col>
			</v-row>
		</Section>
		<Section
        :title="'Contact us'" :id="'contact-us'" :dark="'theme--dark'"
        :styles="'grey darken-4 white--text theme--dark'">
			<ContactUsForm></ContactUsForm>
			<div class="py-12"></div>
		</Section>
		<v-footer
				absolute
				class="font-weight-medium  grey darken-1"
		>
			<v-col
					class="text-center"
					cols="12"
			>
				{{ new Date().getFullYear() }} — <strong>ViTiler</strong>
			</v-col>
		</v-footer>
	</v-container>
</template>

<script>
  import Section from "@/components/Section";
  import ContactUsForm from "@/components/ContactUsForm";

  export default {
    name: "Portfolio",
    components: {
      ContactUsForm,
      Section,
    },
    data() {
      return {
        colors: [
          'grey',
          'secondary',
          'grey darken-2',
        ],
        slides: [
          'First',
          'Second',
          'Third',
        ],
        posts: [
          {
            img: 'img/mosaic-2.jpg',
            text: 'Vuetify is the #1 component library for Vue.js and has been in active development since 2016.'
          },
          {
            img: 'img/shower.jpg',
            text: 'Vuetify is the #1 component library for Vue.js and has been in active development since 2016.'
          },
          {
            img: 'img/shower-cabin.jpg',
            text: 'Vuetify is the #1 component library for Vue.js and has been in active development since 2016.'
          },
          {
            img: 'img/white-tile.jpg',
            text: 'Vuetify is the #1 component library for Vue.js and has been in active development since 2016.'
          }
        ]
      }
    },
  }
</script>

<style scoped>

</style>
