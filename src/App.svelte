<script>
	import ToDoInputForm from "./ToDoInputForm.svelte";
	import ToDoList from "./ToDoList.svelte";
	let nameEntered = false;

	let userName = '';
	let password = '';
	let errorStr = '';

	function handleSubmit() {
		if (!userName|| !password) {
			errorStr = '未入力の項目があります';
			return;
		}
		// APIでログイン情報取得







		nameEntered = true;
	}
</script>

<main>
	<div>
{#if nameEntered}
	<div>
		<h1>Your Task</h1>
		<h3>user&nbsp;:&nbsp;{userName}</h3>
	</div>
	<ToDoInputForm userName={userName} />
	<ToDoList />
{:else}
	<h1>Your Task</h1>
	<div>
		<span class="error">{errorStr}</span>
	</div>
	<form on:submit|preventDefault={handleSubmit}>
		<div>
			<input bind:value={userName} type="text" placeholder="user name">
		</div>
		<div>
			<input bind:value={password} type="text" placeholder="password">
		</div>
		<button type="submit">タスク管理を始める</button>
	</form>
{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 450px;
		margin: 0 auto;
	}
	.error {
		color: red;
	}
</style>