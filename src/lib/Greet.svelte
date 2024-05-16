<script lang="ts">
	import { invoke } from "@tauri-apps/api/core";

	$: name = "";
	$: greetMsg = "";

	async function sayHello() {
		greetMsg = await invoke("greet", { name: name });
	}
</script>

<input bind:value={name} type="text" id="name" placeholder="Enter your name" />
<button on:click={sayHello}>Say Hello</button>
<p>{greetMsg}</p>
