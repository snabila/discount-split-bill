<script>
    export let objAttributes;
	import { createEventDispatcher } from "svelte";

	const dispatch = createEventDispatcher();

	function deleteItem() {
		dispatch('deleteItem', {objAttributes})
	}
</script>

<div id="field-{objAttributes.id}" class="item">
    <!-- [{ id: 1, label: '', price: 0, unit: 0, knownPrice: 0, knownUnit: 0 }] -->

	<div class="item-id">
		<p>#{objAttributes.id}</p>
		<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" on:click={deleteItem}>
			<path stroke-linecap="round" stroke-linejoin="round" d="m14.74 9-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 0 1-2.244 2.077H8.084a2.25 2.25 0 0 1-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 0 0-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 0 1 3.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 0 0-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 0 0-7.5 0" />
		</svg>			  
	</div>

	<!-- Item name -->
	<div>
		<label for="field-{objAttributes.id}-name">
			Name
		</label>
		<input
			placeholder="Item {objAttributes.id}"
			type="text"
			id="field-{objAttributes.id}-name"
			bind:value={objAttributes.label}
			required
		/>
	</div>

    <!-- Item price -->
	<div>
		<label for="field-{objAttributes.id}-price">
			Regular Price
		</label>
		<input
			placeholder="Item {objAttributes.price}"
			type="number"
			id="field-{objAttributes.id}-price"
			bind:value={objAttributes.price}
			required
		/>
	</div>
</div>

<style>
    .item {
        padding: 24px;
        background-color: var(--color-bg-1);
        /* border: solid 1px var(--color-text-2); */
		border-radius: 4px;
    }

    .item:not(:last-child) {
        margin-bottom: 24px;
    }

    .item div:not(:last-child) {
        margin-bottom: 16px;
    }

	.item-id {
		display: flex;
		justify-content: space-between;
		font-size: 12px;
	}

	.item-id svg {
		width: 16px;
		cursor: pointer;
	}

	label {
		font-size: 14px;
	}

</style>