<template>
	<v-responsive>
		<ValidationObserver v-slot="{ handleSubmit }" ref="form">
			<v-form

					lazy-validation
					v-model="form.valid"
					@submit.prevent="handleSubmit(onSubmit)"

			>
				<v-row>
					<v-col sm="10" md="6" offset-sm="1" offset-md="3">
						<ValidationProvider rules="required" v-slot="{ errors }">
							<v-text-field
									v-model="form.name"
									label="Name*"
									solo
									:error-messages="errors"
							></v-text-field>
						</ValidationProvider>
					</v-col>
				</v-row>
				<v-row>
					<v-col sm="10" md="6" offset-sm="1" offset-md="3">
						<ValidationProvider rules="required|email" v-slot="{ errors }">
							<v-text-field
									label="E-mail*"
									pattern="([A-z0-9_.-]{1,})@([A-z0-9_.-]{1,}).([A-z]{2,8})"
									:error-messages="errors"
									v-model="form.email"
									solo
							></v-text-field>
						</ValidationProvider>
					</v-col>
				</v-row>
				<v-row>
					<v-col sm="10" md="6" offset-sm="1" offset-md="3">
						<ValidationProvider rules="required" v-slot="{ errors }">
							<v-textarea
									no-resize
									height="200"
									label="Text*"
									v-model="form.text"
									:error-messages="errors"
									solo
							></v-textarea>
						</ValidationProvider>
					</v-col>
				</v-row>

				<v-btn
						type="submit"
						color="green lighten-1"
						class="mr-4"
				>
					Submit
				</v-btn>
				<v-btn
						color="orange lighten-3"
						@click="resetForm"
				>
					Reset
				</v-btn>
			</v-form>
		</ValidationObserver>
	</v-responsive>
</template>

<script>
  import {ValidationObserver, ValidationProvider, extend} from 'vee-validate';

  extend('required', {
    validate(value) {
      return {
        required: true,
        valid: ['', null, undefined].indexOf(value) === -1,
      };
    },
    message: 'Require field',
    computesRequired: true
  });

  extend('email', {
    validate(value) {
      const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

      return {
        valid: pattern.test(value)
      }
    },
    message: 'Incorrect e-mail address'
  })

  export default {
    name: "ContactUsForm",
    components: {
      ValidationProvider,
      ValidationObserver
    },
    data() {
      return {
        form: {
          name: '',
          email: '',
          text: '',
        }
      }
    },
    computed: {},
    methods: {
      onSubmit() {
        console.log('Form Submitted!')
      },
      resetForm() {
        this.form = {
          name: '',
          email: '',
          text: ''
        }
        this.$nextTick(() => {
          this.$refs.form.reset()
        })
      }
    }
  }
</script>

<style scoped>

</style>
