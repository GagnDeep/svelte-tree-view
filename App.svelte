<script>
  import Tree from "./TreeView";

  const tree = [
    {
      name: "This is a root node",
      children: [
        {
          name: "And it has"
        },
        {
          name: "two children"
        }
      ]
    },
    {
      name: "This is another root node",
      children: [
        {
          name: "This one is alone"
        },
        {
          name: "But this one has nested children",
          children: [
            {
              name: "Like this"
            },
            {
              name: "and this"
            }
          ]
        }
      ]
    }
  ];
</script>
<Tree itemClasses="pl-5" {tree} let:node let:toggle let:expanded let:hasChildren>
</Tree>
<svelte:head>
	<link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css" rel="stylesheet">
</svelte:head>
