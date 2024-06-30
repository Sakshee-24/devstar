<script>

	var reqfunc;  //Select encrypt decrypt
	
	var output;   //output
	  
		function encryptdecrypt(input){
			if (reqfunc=="encrypt") {
	/* -----------------ENCRYPTION--------------------- */
	
				output = btoa(input.target.value);
			}
			else if (reqfunc=="decrypt") {
	/* -----------------DECRYPTION--------------------- */
	
				output = atob(input.target.value);
			}
		}
	
		
	  </script>
	  
	
	
	  <body class="bg-white dark:bg-gray-900">
		<div class="py-20 px-4 mx-auto max-w-screen-xl lg:px-12 grid space-y-10">
			<h1 class="text-3xl sm:text-4xl font-bold tracking-tight leading-none text-gray-900 dark:text-white">
			   Text Encryption / Decryption Tool
			</h1>
			
			</div>
	
		<div class="py-12 px-4 mx-auto rounded-lg overflow-hidden border border-gray-300 mx-auto max-w-screen-xl lg:px-12">
	
			<div class="card p-8  relative items-center mx-auto max-w-screen-xl overflow-hidden rounded-lg">
	
				<div class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
					<select bind:value={reqfunc} class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
	
							<option value="encrypt">Encrypt</option>
							<option value="decrypt">Decrypt</option>
	
					</select>
				</div>
	
				<div class="mt-4 gap-4 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden">
	
					<div class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
						<textarea placeholder="Enter Text" id="textbox" rows="8" class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						on:input={encryptdecrypt}/>
					</div>
	
					<div class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
						<textarea placeholder="Result" id="textbox" rows="8" class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
						bind:value={output}/>
					</div>
				   
	
				</div>
				
				
	
			</div>
		</div>
	</body>
	  
	  