<script>
  let result = ''
  const correctAnswer = 'b'
  const answers = ['a', 'b', 'c', 'd']
  let quiz = getQuiz()

  /**
   * @param {string} answer
   */
  function pickAnswer(answer) {
    console.log(`answered ${answer}`)
    if (correctAnswer === answer) {
      result = 'Correct!'
    } else {
      result = 'OOPS'
    }
  }

  async function getQuiz() {
    const res = await fetch(
      'https://opentdb.com/api.php?amount=10&category=12&type=multiple'
    )
    const data = await res.json()
    console.log({ data })

    return data
  }

  function handleClick() {
    quiz = getQuiz()
  }
</script>

<button on:click={handleClick}>Get new questions</button>
<h3>
  {#await quiz}
    Loading...
  {:then data}
    {data.results[0].question}
  {/await}
</h3>

<div>
  {#if result}
    <h4>{result}</h4>
  {:else}
    <h5>Please pick an answer</h5>
  {/if}
  {#each answers as answer}
    <button on:click={() => pickAnswer(answer)}>
      Answer {answer.toUpperCase()}
    </button>
  {/each}
</div>

<style>
  h4 {
    color: red;
  }
</style>
