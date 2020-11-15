<script>
  import TreeNode from "./TreeNode.svelte";
  export let tree = [];

  export let itemClasses = "";
</script>

<style>
  .button {
    opacity: 0;
  }
  .node:hover .button {
    opacity: 1;
  }
  .button.collapsed {
    transform: rotateZ(-90deg);
  }
</style>

{#each tree as _node, i}
  <TreeNode {itemClasses} node={_node} index={i} let:node let:toggle let:open let:close let:index let:hasChildren let:expanded>
    <slot {node} {toggle} {expanded} {close} {open} {index} {hasChildren}>
      <div class="flex items-center node">
        <div class="w-5">
          {#if hasChildren}
            <div on:click={toggle} class="h-5 w-5 cursor-pointer text-red-600 button" class:collapsed={!expanded}>
              <svg focusable="false" viewBox="0 0 24 24">
                <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" />
              </svg>
            </div>

          {/if}
        </div>

        <div class="content">{node.name}</div>
      </div>
      
    </slot>
  </TreeNode>
{/each}