<script>
	export let productName, productDescription, category, id;
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	const remove = () => dispatch('remove', id);
	const edit = () => dispatch('edit', id);
</script>

<article {id}>
	<aside>{`${category.charAt(0).toUpperCase()}${category.slice(1)}`}</aside>
	<div class="info">
		<img src={`${category}.webp`} alt={productName} />
		<h2>{productName}</h2>
		<p>{productDescription}</p>
		<div class="main_btn">
			<button on:click={edit} type="button"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					class="icon icon-tabler icon-tabler-edit"
					width="24"
					height="24"
					viewBox="0 0 24 24"
					stroke-width="2"
					stroke="currentColor"
					fill="none"
					stroke-linecap="round"
					stroke-linejoin="round"
				>
					<path stroke="none" d="M0 0h24v24H0z" fill="none" />
					<path d="M7 7h-1a2 2 0 0 0 -2 2v9a2 2 0 0 0 2 2h9a2 2 0 0 0 2 -2v-1" />
					<path d="M20.385 6.585a2.1 2.1 0 0 0 -2.97 -2.97l-8.415 8.385v3h3l8.385 -8.415z" />
					<path d="M16 5l3 3" />
				</svg></button
			>
			<button on:click={remove} type="button"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					class="icon icon-tabler icon-tabler-trash-filled"
					width="24"
					height="24"
					viewBox="0 0 24 24"
					stroke-width="2"
					stroke="currentColor"
					fill="none"
					stroke-linecap="round"
					stroke-linejoin="round"
				>
					<path stroke="none" d="M0 0h24v24H0z" fill="none" />
					<path
						d="M20 6a1 1 0 0 1 .117 1.993l-.117 .007h-.081l-.919 11a3 3 0 0 1 -2.824 2.995l-.176 .005h-8c-1.598 0 -2.904 -1.249 -2.992 -2.75l-.005 -.167l-.923 -11.083h-.08a1 1 0 0 1 -.117 -1.993l.117 -.007h16z"
						stroke-width="0"
						fill="currentColor"
					/>
					<path
						d="M14 2a2 2 0 0 1 2 2a1 1 0 0 1 -1.993 .117l-.007 -.117h-4l-.007 .117a1 1 0 0 1 -1.993 -.117a2 2 0 0 1 1.85 -1.995l.15 -.005h4z"
						stroke-width="0"
						fill="currentColor"
					/>
				</svg></button
			>
		</div>
	</div>
</article>

<style>
	article {
		display: flex;
		width: 33%;
		max-width: 41rem;
		min-height: 27rem;
		height: auto;
		max-height: 55rem;
		background-color: var(--input-bg);
		color: var(--card-color);
	}

	.info {
		display: flex;
		flex-direction: column;
		justify-content: start;
		align-items: center;
		gap: 1.5rem;
		width: 100%;
		padding: 1rem;
	}

	.info * {
		margin: 0;
	}

	.info img {
		width: 12rem;
		height: 12rem;
		object-fit: cover;
		border-radius: 50%;
	}

	.info h2 {
		font-size: 1.1em;
		text-transform: uppercase;
		text-align: center;
	}

	.info p {
		align-self: flex-start;
		font-size: 0.75em;
		font-weight: 200;
	}

	aside {
		width: min-content;
		height: 100%;
		padding: 0 0.5rem;
		background-color: red;
		writing-mode: vertical-lr;
		text-align: center;
		font-size: 2rem;
		font-weight: bold;
	}
	.main_btn {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		margin-top: auto;
	}

	.main_btn button {
		min-width: auto;
		width: 45%;
		outline: none;
		border-radius: 0.5rem;
	}

	.main_btn button:first-child {
		background-color: #8a2be2;
	}

	.main_btn button:last-child {
		background-color: #ff0000;
	}

	@media screen and (max-width: 50rem) {
		article {
			width: 100%;
		}
	}
</style>
