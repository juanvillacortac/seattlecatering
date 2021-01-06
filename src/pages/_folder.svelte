<script>
  import Navbar, { height, transparent } from '../components/navigation/Navbar.svelte'
  import Footer from '../components/Footer.svelte'
  import { isActive, isChangingPage } from '@roxi/routify/runtime'
  import { afterPageLoad } from "@roxi/routify"
  import { preferences } from '../stores/preferences'
  import { goto } from '@roxi/routify'
  import NProgress from 'nprogress'

  $: protectedRoute = $isActive('/order')

  $: granted = ($preferences.auth && protectedRoute) || !protectedRoute

  NProgress.configure({
    // Pass in your configuration here, below is just how I like it
    // Full list: https://github.com/rstacruz/nprogress#configuration
    minimum: 0.16,
    showSpinner: false,
  })

  $: {
    if ($isChangingPage) {
      NProgress.start()
    } else {
      NProgress.done()
    }
  }


  let padded
  $afterPageLoad(() => {
      $transparent = (($isActive('/index') && !$preferences.auth) || $isActive('/menu/:category/:meal')) && granted
      padded = !$transparent
  })
</script>

<div class="flex flex-col w-full min-h-screen">
  <Navbar/>
  <main class="flex justify-center flex-grow w-full h-full overflow-hidden" style="margin-top: {padded ? $height : 0}px">
    {#if !granted}
      {$goto('/login')}
    {:else}
      <slot/>
    {/if}
  </main>
  <div oneWay class="w-full animate" style="--animate-y: 20%">
    <img src="/images/seattle.svg" alt="" class="w-full pointer-events-none select-none">
  </div>
  <!--Footer/-->
</div>
