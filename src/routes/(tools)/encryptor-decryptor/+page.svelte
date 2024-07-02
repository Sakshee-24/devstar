<script>
	export let data;
	let isChecked1 = false; //to enable secret key
	let isChecked2 = false; //to enable secret key

	var encryptOutput; //Encryption output variable
	var decryptOutput; //Decryption output variable

	function encrypt(input) {
		/* -----------------ENCRYPTION--------------------- */

		encryptOutput = btoa(input.target.value);
	}

	function decrypt(input) {
		/* -----------------DECRYPTION--------------------- */

		decryptOutput = atob(input.target.value);
	}
</script>

<section class="bg-white dark:bg-gray-900">
	<div class=" px-4 mx-auto mx-auto max-w-screen-xl lg:px-12">
		<div
			class="card p-8 relative items-center mx-auto max-w-screen-xl overflow-hidden rounded-lg"
		>
			<div
				class="gap-4 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden"
			>
				<!-- Headings -->
				<h1
					class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white"
				>
					Text Encryption
				</h1>
				<h1
					class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white"
				>
					Text Decryption
				</h1>
				<!-- Input -->
				<div
					class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Enter Text to be Encrypted"
						id="textbox"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						on:input={encrypt}
					/>
				</div>

				<div
					class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Enter Text to be Decrypted"
						id="textbox"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						on:input={decrypt}
					/>
				</div>

				<!-- Secret key Enable/Disable -->
				<div class="flex items-center">
					<div class="flex items-center">
						<input
							id="myCheckbox1"
							type="checkbox"
							class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
							bind:checked={isChecked1}
						/>
						<label
							for="myCheckbox1"
							class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
							>Encrypt with a custom secret key</label
						>
					</div>
				</div>

				<div class="flex items-center">
					<div class="flex items-center">
						<input
							id="myCheckbox2"
							type="checkbox"
							class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
							bind:checked={isChecked2}
						/>
						<label
							for="myCheckbox2"
							class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
							>Decryption requires a custom secret key</label
						>
					</div>
				</div>
				<!-- Secret Key TextArea -->
				<textarea
					id="myTextarea1"
					placeholder="Enter Secret Key"
					rows="1"
					class="resize-none block p-2.5 w-full text-sm text-gray-900 {isChecked1
						? 'bg-gray-50'
						: 'bg-gray-200'} rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500
  dark:{isChecked1
						? 'bg-gray-700'
						: 'bg-gray-800'} dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
					disabled={!isChecked1}
				/>

				<textarea
					id="myTextarea2"
					placeholder="Enter Secret Key"
					rows="1"
					class="resize-none block p-2.5 w-full text-sm text-gray-900 {isChecked2
						? 'bg-gray-50'
						: 'bg-gray-200'} rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500
    dark:{isChecked2
						? 'bg-gray-700'
						: 'bg-gray-800'} dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
					disabled={!isChecked2}
				/>
				<!-- Output Buttons -->
				<div>
					<button
						type="button"
						class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
				
				on:click={() => encrypt()}> Encrypt</button
					>
				</div>
				<div>
					<button
						type="button"
						class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
					
					on:click={() => decrypt()}> Decrypt</button
					>
				</div>
				<!-- Result -->
				<div
					class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Encrypted Output"
						rows="8"
						class="max-h-20 resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
					/>
				</div>

				<div
					class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Decrypted Output"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
					/>
				</div>
			</div>

			<div
				class="items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-1 overflow-hidden"
			></div>
		</div>
	</div>
</section>
