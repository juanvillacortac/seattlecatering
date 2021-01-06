<script>
  import { transparent } from '../components/navigation/Navbar.svelte'
  import svitsConfig from '../../svits.config'
  import { preferences } from '../stores/preferences'
  import { metatags } from '@roxi/routify'
  import Title from '../components/Title.svelte'
  import { fly } from 'svelte/transition'
  import Image from '../components/Image.svelte'

  metatags.title = 'About us | ' + svitsConfig.name

  // import { getCollection } from '../collections'

  $: dark = $preferences.darkMode

  const inArgs = {y: -10, duration: 500, delay: 100}
</script>

<div class="content" in:fly={inArgs}>
  <div class="hidden mb-6 md:mb-24 md:block">
    <Title first="About us" second="Know us"/>
  </div>
  <div class="flex flex-col items-center mb-12 md:flex-row">
    <div class="py-6 md:w-1/2">
      <Title first="Since 2003" second="Who we are"/>
    </div>
    <p class="text-lg text-justify text-gray-500 md:w-1/2">
    <strong>Seattle Corporate Catering</strong>  is the online ordering portal for Seattle's best and most reliable catering company. The company was created in 2003.   It is such a thrill to throw an important party or cater a meal that meets our client's high expectations.  It was the joy and passion that comes from this thrill that drove us to create this great Seattle catering company.
    </p>
  </div>
  <div class="flex flex-col items-center mb-12 md:flex-row-reverse">
    <div class="py-6 md:w-1/2">
      <Title first="Know us" second="Our mission"/>
    </div>
    <p class="text-lg text-justify text-gray-500 md:w-1/2">
    With the <strong>Seattle Corporate Catering</strong> website we have made it easier and quicker for our corporate catering clients to place and track their event orders. If you are planning a large confersiness meeting, ence or just a meal for a regularily scheduled business meeting, treat your attendees to great food and flavor. SCC will confirm your online order and guarantee the success of your important event. 
    </p>
  </div>
</div>
