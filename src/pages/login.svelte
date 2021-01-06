<script>
  import svitsConfig from '../../svits.config'
  import { preferences } from '../stores/preferences'
  import { metatags, goto, url } from '@roxi/routify'
  import Title from '../components/Title.svelte'
  import { fly } from 'svelte/transition'
  import V from '../components/IntersectingViewport.svelte'

  metatags.title = 'Log in | ' + svitsConfig.name

  const inArgs = {y: -10, duration: 500, delay: 100}

  let email = false
  const auth = $preferences.auth

  const login = () => {
    $goto('/index')
    $preferences.auth = {
      business: 'google',
    }
  }
</script>

<style>
  .input {
    @apply text-gray-600;
    @apply placeholder-gray-300;
    @apply bg-transparent;
    @apply border-b;
    @apply transition-colors;
    @apply border-gray-300;
    @apply duration-200;
  }

  .input:focus {
    @apply border-gray-600;
    outline: none;
  }

  :global(.dark .input) {
    @apply border-gray-600;
    @apply placeholder-gray-600;
    @apply text-gray-500;
  }

  :global(.dark .input:focus) {
    @apply border-gray-500;
  }

  .huge {
    font-size: 12rem;
  }

  .e404 {
    text-align: center;
    @apply text-gray-700;
  }

  :global(.dark .e404) {
    @apply text-gray-400;
  }
</style>

{#if auth}
  <div class="flex w-full">
    <div class="py-16 m-auto overflow-hidden e404">
      <div class="leading-none text-gray-500 i jam:cactus huge" in:fly={{y: -20, duration: 800}}></div>
      <div class="flex flex-col items-center big">
        You're currently logged in
        <!-- link to the parent folder of _fallback.svelte -->
        <a class="text-blue-600 hover:underline" href={$url('/index')}>Go to home -&gt</a>
      </div>
    </div>
  </div>
{:else}
  <div class="content" in:fly={inArgs}>
    <div class="mb-16">
      <Title first="Welcome" second="Log in to our services"/>
    </div>
    <V class="flex px-4 mb-16 animate" oneWay style="--animate-s: 0.9">
      <div
        class="flex flex-col w-full p-4 m-auto text-gray-500 border shadow md:w-4/10 xxl:w-3/10 rounded-2xl dark:border-gray-700"
      >
        {#if !email}
          <button
            on:click={() => login()}
            style="border-width: 2px"
            class="flex items-center justify-center py-2 mb-4 text-green-500 border border-green-500 snipcart-add-item duration-200 hover:bg-green-500 hover:text-white rounded-md font-title"
          >Log in with Google</button>

          <button class="font-bold text-left text-blue-500 hover:underline" on:click={() => email = true }>Or log in with an email direction -&gt</button>
        {:else}
          <button class="mb-4 font-bold text-left text-blue-500 hover:underline" on:click={() => email = false }>&lt;- Go back</button>
          <div class="flex flex-col w-full pt-4 border-t border-gray-300 dark:border-gray-600 duration-200">
            <p class="mb-4 font-bold">Log in with an email direction:</p>

            <input type="text" class="mb-6 input" placeholder="Email">

            <input type="password" class="mb-6 input" placeholder="Password">

            <button
              on:click={() => login()}
              class="btn"
            >Log in</button>
          </div>
        {/if}
      </div>
    </V>
  </div>
{/if}
