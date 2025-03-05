<script lang="ts">
	import FormField from './registerFormField.svelte'
	import GoBackButton from '../general/goBackButton.svelte'
	import Button from './registerButton.svelte'
	//import Captcha from './registerCaptcha.svelte';
	import PolicyText from './registerPolicyText.svelte'
	import { idOptions } from '../vars.ts'
	import { participationOptions } from '../vars.ts'
	import { topicOptions } from '../vars.ts'

	interface FormData {
		name: string
		lastName: string
		identificationType: string
		identificationNumber: string
		email: string
		institution: string
		city: string
		country: string
		address: string
		participationType: string
		password: string
		repeatPassword: string
	}
	const idTypes = ['CC', 'Passport', 'Other']
	const pTypes = ['Regular participant', "Undergraduate, Master's, and Doctoral Students"]

	let formData: FormData = {
		name: '',
		lastName: '',
		identificationType: '',
		identificationNumber: '',
		email: '',
		institution: '',
		city: '',
		country: '',
		address: '',
		participationType: '',
		password: '',
		repeatPassword: ''
	}

	function handleSubmit() {
		// Handle form submission
	}
</script>

<main class="flex overflow-hidden flex-col items-center px-20 pt-8 bg-white max-md:px-5">
	<div class="lg:relative top-[64px] flex flex-col w-full max-w-[1136px] max-md:max-w-full">
		<section class="flex flex-col py-20 w-full max-md:max-w-full">
			<div class="flex flex-col w-full font-semibold text-indigo-900 max-md:max-w-full">
				<GoBackButton />
				<h1 class="mt-2 text-5xl leading-none max-md:max-w-full max-md:text-4xl">Register Form</h1>
			</div>

			<form
				on:submit|preventDefault={handleSubmit}
				class="flex flex-col mt-8 w-full text-sm max-md:max-w-full"
			>
				<div class="flex flex-wrap gap-5 items-center w-full max-md:max-w-full">
					<FormField
						label="Name*"
						type="text"
						bind:value={formData.name}
						placeholder="John"
						required
					/>
					<FormField
						label="Last Name*"
						type="text"
						bind:value={formData.lastName}
						placeholder="Doe"
						required
					/>
					<!--
					<FormField
						label="Second Name"
						type="text"
						bind:value={formData.secondName}
						placeholder="John"
					/>
					-->
				</div>

				<!--
				<FormField
					label="Second Last Name"
					type="text"
					bind:value={formData.secondLastName}
					placeholder="Doe"
				/>
				-->

				<div class="flex flex-wrap gap-5 items-center mt-4 w-full max-md:max-w-full">
					<FormField
						label="Identification Type*"
						type="select"
						bind:value={formData.identificationType}
						options={idOptions}
						placeholder="Select your identification type"
						required
					/>
					<FormField
						label="Identification Number*"
						type="text"
						bind:value={formData.identificationNumber}
						placeholder="Write your identification number"
						required
					/>
				</div>

				<div class="flex flex-wrap gap-5 items-center mt-4 w-full max-md:max-w-full">
					<FormField
						label="E-Mail*"
						type="email"
						bind:value={formData.email}
						placeholder="name@address.com"
						required
					/>
					<FormField
						label="Institution*"
						type="text"
						bind:value={formData.institution}
						placeholder="Write the name of your institution, filial or company"
						required
					/>
				</div>

				<div class="flex flex-wrap gap-5 items-center mt-4 w-full max-md:max-w-full">
					<FormField
						label="City*"
						type="text"
						bind:value={formData.city}
						placeholder="City Name"
						required
					/>
					<FormField
						label="Country*"
						type="text"
						bind:value={formData.country}
						placeholder="Country Name"
						required
					/>
				</div>

				<div class="flex flex-wrap gap-5 items-center mt-4 w-full max-md:max-w-full">
					<FormField
						label="Correspondence Address*"
						type="text"
						bind:value={formData.address}
						placeholder="Write your correspondence address"
						required
					/>
					<FormField
						label="Participation type*"
						type="select"
						bind:value={formData.participationType}
						options={participationOptions}
						placeholder="Select a participation type"
						required
					/>
				</div>

				<div class="flex flex-wrap gap-5 items-center mt-4 w-full max-md:max-w-full">
					<FormField
						label="Password*"
						type="password"
						bind:value={formData.password}
						placeholder="Write your password"
						required
					/>
					<FormField
						label="Repeat password*"
						type="password"
						bind:value={formData.repeatPassword}
						placeholder="Repeat your password"
						required
					/>
				</div>

				<!-- <Captcha /> -->
				<button
					class="g-recaptcha"
					data-sitekey="PUBLIC_SITE_KEY"
					data-callback="onSubmit"
					data-action="submit"
				>
					Click me to verify the captcha challenge!
				</button>

				<div class="flex gap-4 justify-center items-center mt-4 text-sm text-white">
					<Button type="submit" variant="primary">Sign Up</Button>
				</div>
			</form>

			<PolicyText />
		</section>
	</div>
</main>

<style>
	:global(builder-component) {
		max-width: none !important;
	}
</style>
