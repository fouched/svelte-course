<script>
  let count = 0

  $: counterString = `You have clicked ${count} times`

  function increment() {
    ++count
  }
</script>

<button on:click={increment}>Clicks {count}</button>
<h3>{counterString}</h3>