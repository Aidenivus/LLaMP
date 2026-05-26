<script>
  export let structure = null;

  $: formula = structure?.formula_pretty || structure?.composition_reduced || 'Unknown';
  $: material_id = structure?.material_id || '';
  $: spacegroup = structure?.symmetry?.symbol || structure?.spacegroup?.symbol || '';
  $: nsites = structure?.nsites || '';
  $: energy = structure?.energy_per_atom;
</script>

<div class="card p-3 variant-soft-surface" style="max-width: 280px;">
  <h4 class="font-bold text-sm">{formula}</h4>
  {#if material_id}
    <p class="text-xs opacity-70">
      <a
        href="https://next-gen.materialsproject.org/materials/{material_id}"
        class="underline text-blue-600 hover:opacity-75"
        target="_blank"
        rel="noopener noreferrer"
      >
        {material_id}
      </a>
    </p>
  {/if}
  {#if spacegroup}
    <p class="text-xs opacity-70">Space group: {spacegroup}</p>
  {/if}
  {#if nsites}
    <p class="text-xs opacity-70">Sites: {nsites}</p>
  {/if}
  {#if energy}
    <p class="text-xs opacity-70">Energy: {energy.toFixed(3)} eV/atom</p>
  {/if}
</div>
