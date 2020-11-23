<script>
	import material_base from './data/materials_base.js';
	import material_lvl_2 from './data/materials_lvl_2.js';
	import material_lvl_3 from './data/materials_lvl_3.js';
  import structures from './data/structures.js';

	let material_count = material_base.length;

	function getMaterials(lvl2_id) {
		for (var i = 0; i < material_count; i++) {
			if (lvl2_id === material_base[i].id) {
				return material_base[i].name;
			}
		}
	}
</script>

<main>
	<div id="level-2">
		<h1>Level 1</h1>
		{#each material_base as base }
			<div class="levelCard">
				<h2>{ base.name }</h2>
			</div>
		{/each}
	</div>
	<div id="level-1">
		<h1>Level 2</h1>
		{#each material_lvl_2 as mat }
			<div class="levelCard">
				<h2>{ mat.name }</h2>
				{#each mat.materials as item}
					{#if item.type == 'material_base'}
						<h4>{ getMaterials(item.id) } - { item.qty }</h4>
					{/if}
				{/each}
			</div>
		{/each}
	</div>
	<div id="level-3">
		<h1>Level 3</h1>
		{#each material_lvl_3 as mat }
			<div class="levelCard">
				<h2>{ mat.name }</h2>
				{#each mat.materials as item}
					<h4>{ item.id } - { item.qty }</h4>
				{/each}
			</div>
		{/each}
	</div>
	<div id="level-4">
		<h1>Level 4</h1>
		{#each material_lvl_2 as mat }
			<div class="levelCard">
				<h2>{ mat.name }</h2>
				{#each mat.materials as item}
					{#if item.type == 'material_base'}
						<h4>{ getMaterials(item.id) } - { item.qty }</h4>
					{/if}
				{/each}
			</div>
		{/each}
	</div>
</main>

<style>
	main {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: center;
		align-content: space-between;
		width: 100%;
		height: 100%;
	}

	#level-1, #level-2, #level-3, #level-4 {
		width: 20rem;
	}

</style>
