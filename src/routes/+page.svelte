<script>
	import Form from '../lib/form.svelte';
	import Card from '../lib/card.svelte';

	// VARIABLES
	let productEditionState = false;
	let idEditableElement;
	let allProducts = [];
	let product = {};

	// FONCTIONS

	const cleanFormElement = () => {
		const formElem = document.querySelector('form');
		const selectElem = formElem.querySelector('select');
		formElem.reset();
		selectElem.selectedIndex = 0;
	};

	const addProduct = (event) => {
		product = event.detail;
		allProducts = [...allProducts, product];
		cleanFormElement();
	};

	const updateProduct = (event) => {
		product = event.detail;
		const newProduct = {
			productName: product.productName,
			productDescription: product.productDescription,
			category: product.category,
			id: product.id
		};
		const productIndex = allProducts.findIndex((prod) => prod.id === idEditableElement);
		allProducts[productIndex] = newProduct;
		productEditionState = false;
		cleanFormElement();
	};

	const handleFormSubmit = (e) => {
		if (!productEditionState) {
			addProduct(e);
		} else {
			updateProduct(e);
		}
	};

	const deleted = (e) => {
		const id = e.detail;
		return (allProducts = allProducts.filter((product) => product.id !== id));
	};

	const edit = (e) => {
		productEditionState = true;
		idEditableElement = e.detail;
	};
</script>

<main>
	<section class="products">
		{#each allProducts as { productName, productDescription, category, id }, i}
			<Card {productName} {productDescription} {category} {id} on:remove={deleted} on:edit={edit} />
		{/each}
	</section>
	<Form bind:product on:formSubmit={handleFormSubmit} {productEditionState} />
</main>

<style>
	main {
		display: grid;
		grid-template-rows: 1fr min-content;
		gap: 2rem;
		min-height: 100vh;
		padding: 2rem;
	}

	.products {
		margin-bottom: auto;
		display: flex;
		flex-wrap: wrap;
		justify-content: flex-start;
		align-items: center;
		gap: 1rem;
	}

	@media screen and (max-width: 600px) {
		main {
			justify-content: center;
		}

		.products {
			justify-content: center;
		}
	}
</style>
