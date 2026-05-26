<script>
  export let structure = null;
  export let camera_position = { x: 3, y: 3, z: 3 };
  export let show_image_atoms = false;
  export let show_bonds = true;

  $: formula = structure?.formula_pretty || structure?.composition_reduced || 'Unknown';
  $: nsites = structure?.nsites || '?';
  $: lattice = structure?.lattice;
</script>

<div
  class="structure-placeholder"
  style="
    width: var(--struct-width, 280px);
    height: var(--struct-height, 280px);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
    border-radius: 12px;
    color: #e0e0e0;
    font-family: system-ui, sans-serif;
    border: 1px solid #333;
    position: relative;
    overflow: hidden;
  "
>
  <div style="font-size: 2.5rem; margin-bottom: 0.5rem;">🔬</div>
  <div style="font-size: 1.2rem; font-weight: bold; color: #64b5f6;">
    {formula}
  </div>
  {#if nsites !== '?'}
    <div style="font-size: 0.85rem; opacity: 0.7; margin-top: 0.25rem;">
      {nsites} sites
    </div>
  {/if}
  {#if lattice}
    <div style="font-size: 0.75rem; opacity: 0.5; margin-top: 0.5rem; text-align: center; padding: 0 1rem;">
      a={lattice.a?.toFixed(2)}Å b={lattice.b?.toFixed(2)}Å c={lattice.c?.toFixed(2)}Å
    </div>
  {/if}
  <div style="position: absolute; bottom: 8px; font-size: 0.65rem; opacity: 0.4;">
    3D view unavailable (elementari)
  </div>
</div>
