<script>
  export let node;
  export let index;

  let expanded = true;
  let hasChildren = false;
  export let itemClasses = "";

  const open = () => (expanded = true);
  const close = () => (expanded = false);
  const toggle = () => (expanded = !expanded);

  $: hasChildren = node && node.children && node.children.length;
</script>

<slot {expanded}  {node} {index} {open} {close} {toggle} {hasChildren}>
</slot>

{#if node.children && expanded}
  <div class={itemClasses}>
    {#each node.children as _node, i}
      <svelte:self {itemClasses} node={_node} index={i} let:expanded let:node let:open let:close let:toggle let:index let:hasChildren>
        <slot {node} {toggle} {close} {open} {index} {hasChildren} {expanded}/>
      </svelte:self>
    {/each}
  </div>
{/if}
