<script>
  import svitsConfig from '../../svits.config'
  import { metatags } from '@roxi/routify'

  import { preferences } from '../stores/preferences'

  import NoAuth from '../components/pages/home/NoAuth.svelte'
  import Auth from '../components/pages/home/Auth.svelte'

  metatags.title = svitsConfig.name
</script>

{#if $preferences.auth}
  <Auth/>
{:else}
  <NoAuth/>
{/if}
