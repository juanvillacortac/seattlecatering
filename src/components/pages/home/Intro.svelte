<script>
  import Image from '../../Image.svelte'
  import Title from '../../Title.svelte'
  import V from '../../IntersectingViewport.svelte'
  import { preferences } from '../../../stores/preferences'

  $: dark = $preferences.darkMode
  export let title = true
</script>

<div class="py-12 content" class:pt-0={!title}>
  <V oneWay>
    <div class="animate" style="--animate-y: 4rem">
      {#if title}
        <Title first="Arista Catering" second="Seattle Corporate Catering"/>
      {/if}
      <p class="mt-6 mb-6 text-lg text-2xl leading-none text-center text-gray-500 sm:text-4xl font-title">
      Fresh, Express Catering<br>for Business Meetings & Corporate Events
      </p>
      <Image src="separator{dark ? '-dark' : ''}.png" alt="separator" class="mx-auto mt-16 pointer-events-none select-none"/>
    </div>
  </V>
</div>
