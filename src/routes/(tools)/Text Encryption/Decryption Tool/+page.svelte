<script>
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

<body class="bg-white dark:bg-gray-900">
	<div class="py-14 px-4 mx-auto max-w-screen-xl lg:px-12 grid space-y-10">
		<h1
			class="text-3xl sm:text-4xl font-bold tracking-tight leading-none text-gray-900 dark:text-white"
		>
			Text Encryption / Decryption Tool
		</h1>
		<hr class="h-px my-8 bg-gray-200 border-0 dark:bg-gray-700">

	</div>

	<div
		class="py-4 px-4 mx-auto rounded-lg overflow-hidden border border-gray-300 mx-auto max-w-screen-xl lg:px-12"
	>
		<div
			class="card p-8 relative items-center mx-auto max-w-screen-xl overflow-hidden rounded-lg"
		>
			<div
				class="gap-4 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-3 overflow-hidden"
			>
				<h1
					class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white"
				>
					Text Encryption
				</h1>
				<p></p>
				<h1
					class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white"
				>
					Text Decryption
				</h1>

				<div
					class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Enter Text"
						id="textbox"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						on:input={encrypt}
					/>
				</div>
				<p></p>

				<div
					class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Enter Text"
						id="textbox"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						on:input={decrypt}
					/>
				</div>

				<div
					class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Encrypted Output"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						bind:value={encryptOutput}
					/>
				</div>
				<p></p>

				<div
					class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300"
				>
					<textarea
						placeholder="Decrypted Output"
						rows="8"
						class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						bind:value={decryptOutput}
					/>
				</div>
			</div>

			<div
				class="items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-1 overflow-hidden"
			></div>
		</div>
	</div>
</body>
