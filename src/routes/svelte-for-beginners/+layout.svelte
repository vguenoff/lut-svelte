<script>
  import { page } from '$app/stores'
</script>

<nav>
  <ul>
    <li>
      <a href="{$page.url.pathname}/levelup-quiz">Level Up Quiz</a>
    </li>
  </ul>
</nav>
<slot />
