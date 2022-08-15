<script>
let firstName = 'this';
let middleName = '.';
let lastName = 'me';
let color = 'blue'
let showText = false
let users = [
	{
		id:1,
		name: 'Reuben'
	},
	{
		id:2,
		name: 'Colette'
	},
	{
		id:3,
		name: 'Mr Mo'
	},
	{
		id:4,
		name: 'Minx'
	}
]

$: name = `${firstName}${middleName}${lastName}`

const toggle = ()=> {
	color = color === 'blue'? 'red' : 'blue'
	showText = !showText
	console.log(users.length+1)
	users = [...users, {id:users.length+1, name: 'scrabbles'}]
}
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
	<p>press button to show text</p>
{/if}
	<button on:click = {toggle}>click</button>

	{#each users as user(user.id)}
	<h3>{user.id}: {user.name}</h3>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>