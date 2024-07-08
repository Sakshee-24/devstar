<script>
    import CryptoJS from 'crypto-js';
    export let data;
    let isChecked1 = false; // to enable secret key for encryption
    let isChecked2 = false; // to enable secret key for decryption

    var encryptOutput = ''; // Encryption output variable
    var decryptOutput = ''; // Decryption output variable

    let secretKey1 = ''; // Secret key for encryption
    let secretKey2 = ''; // Secret key for decryption

    function encrypt(input) {
        const text = input.target.value;
        if (isChecked1 && secretKey1) {
            encryptOutput = CryptoJS.AES.encrypt(text, secretKey1).toString();
        } else {
            encryptOutput = btoa(text);
        }
    }

    function decrypt(input) {
        const text = input.target.value;
        if (isChecked2 && secretKey2) {
            try {
                const bytes = CryptoJS.AES.decrypt(text, secretKey2);
                decryptOutput = bytes.toString(CryptoJS.enc.Utf8);
            } catch (e) {
                decryptOutput = 'Invalid secret key or encrypted text';
            }
        } else {
            try {
                decryptOutput = atob(text);
            } catch (e) {
                decryptOutput = 'Invalid encrypted text';
            }
        }
    }
</script>

<section class="bg-white dark:bg-gray-900">
    <div class="px-4 mx-auto max-w-screen-xl lg:px-12">
        <div class="card p-8 relative items-center mx-auto max-w-screen-xl overflow-hidden rounded-lg">
            <div class="gap-4 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden">
                <!-- Headings -->
                <h1 class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white">Text Encryption</h1>
                <h1 class="text-xl font-bold tracking-tight leading-none text-gray-900 dark:text-white">Text Decryption</h1>

                <!-- Input -->
                <div class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
                    <textarea
                        placeholder="Enter Text to be Encrypted"
                        id="encryptTextBox"
                        rows="8"
                        class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        on:input={encrypt}
                    />
                </div>

                <div class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
                    <textarea
                        placeholder="Enter Text to be Decrypted"
                        id="decryptTextBox"
                        rows="8"
                        class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        on:input={decrypt}
                    />
                </div>

                <!-- Secret key Enable/Disable -->
                <div class="flex items-center">
                    <div class="flex items-center">
                        <input
                            id="encryptCheckbox"
                            type="checkbox"
                            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
                            bind:checked={isChecked1}
                        />
                        <label for="encryptCheckbox" class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300">Encrypt with a custom secret key</label>
                    </div>
                </div>

                <div class="flex items-center">
                    <div class="flex items-center">
                        <input
                            id="decryptCheckbox"
                            type="checkbox"
                            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
                            bind:checked={isChecked2}
                        />
                        <label for="decryptCheckbox" class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300">Decryption requires a custom secret key</label>
                    </div>
                </div>

                <!-- Secret Key TextArea -->
                <textarea
                    id="encryptSecretKey"
                    placeholder="Enter Secret Key"
                    rows="1"
                    class="resize-none block p-2.5 w-full text-sm text-gray-900 {isChecked1 ? 'bg-gray-50' : 'bg-gray-200'} rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:{isChecked1 ? 'bg-gray-700' : 'bg-gray-800'} dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    bind:value={secretKey1}
                    disabled={!isChecked1}
                />

                <textarea
                    id="decryptSecretKey"
                    placeholder="Enter Secret Key"
                    rows="1"
                    class="resize-none block p-2.5 w-full text-sm text-gray-900 {isChecked2 ? 'bg-gray-50' : 'bg-gray-200'} rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:{isChecked2 ? 'bg-gray-700' : 'bg-gray-800'} dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    bind:value={secretKey2}
                    disabled={!isChecked2}
                />

                <!-- Output Buttons -->
                <div>
                    <button
                        type="button"
                        class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
                        on:click={() => encrypt({target: document.getElementById('encryptTextBox')})}
                    > Encrypt</button>
                </div>

                <div>
                    <button
                        type="button"
                        class="py-2.5 px-5 me-2 mb-2 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
                        on:click={() => decrypt({target: document.getElementById('decryptTextBox')})}
                    > Decrypt</button>
                </div>

                <!-- Result -->
                <div class="rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
                    <textarea
                        placeholder="Encrypted Output"
                        rows="8"
                        class="max-h-20 resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        value={encryptOutput}
                        readonly
                    />
                </div>

                <div class="max-h-20 rounded-lg overflow-hidden bg-gray-50 border border-gray-300">
                    <textarea
                        placeholder="Decrypted Output"
                        rows="8"
                        class="resize-none block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        value={decryptOutput}
                        readonly
                    />
                </div>
            </div>
        </div>
    </div>
</section>
