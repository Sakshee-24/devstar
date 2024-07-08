<script>
	import { onMount } from 'svelte';
	import CryptoJS from 'crypto-js';
  
	let message = '';
	let secretKey = '';
	let encryptedMessage = '';
	let decryptedMessage = '';
  
	const encryptMessage = () => {
	  encryptedMessage = CryptoJS.AES.encrypt(message, secretKey).toString();
	};
  
	const decryptMessage = () => {
	  const decryptedBytes = CryptoJS.AES.decrypt(encryptedMessage, secretKey);
	  decryptedMessage = decryptedBytes.toString(CryptoJS.enc.Utf8);
	};
  </script>
  
  <main class="p-4">
	<h1 class="text-2xl font-bold mb-4">Encryption and Decryption</h1>
  
	<label class="block mb-2">
	  Message:
	  <input type="text" class="border border-gray-300 rounded px-2 py-1 w-full" bind:value={message} />
	</label>
  
	<!-- <label class="block mb-2">
	  Secret Key:
	  <input type="text" class="border border-gray-300 rounded px-2 py-1 w-full" bind:value={secretKey} />
	</label> -->
  
	<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mr-2" on:click={encryptMessage}>Encrypt</button>
	<button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded" on:click={decryptMessage}>Decrypt</button>
  
	{#if encryptedMessage}
	  <p class="mt-4">Encrypted Message: {encryptedMessage}</p>
	{/if}
  
	{#if decryptedMessage}
	  <p class="mt-4">Decrypted Message: {decryptedMessage}</p>
	{/if}
  </main>