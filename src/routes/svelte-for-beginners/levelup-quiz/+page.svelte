<script>
  import Quiz from '@components/Quiz.svelte'

  export let name = 'World'
</script>

<h1>
  Hello {name}!
</h1>

<h4>H4 outside Quiz component</h4>

<Quiz />

<style>
  h1 {
    color: pink;
  }

  :global(h4) {
    color: green;
  }
</style>
