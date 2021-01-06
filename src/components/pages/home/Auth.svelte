<script>
  import { metatags } from '@roxi/routify'
  import Carousel from '../../carousel/Carousel.svelte'
  import V from '../../IntersectingViewport.svelte'

  import Intro from './Intro.svelte'
  import Banner from './Banner.svelte'
  import Offers from './Offers.svelte'
  import Title from '../../Title.svelte'

  const slides = [
    {
      centered: true,
      img: '/images/hand.svg',
      content: 'Welcome to our catering',
      bg: 'url(/images/bg2.jpg)',
    },
  ]
</script>

<style>
  .hand {
    animation-name: wink;
    animation-duration: 2.5s;
    animation-iteration-count: infinite;
    transform-origin: 70% 70%;
  }

  @keyframes wink {
    0% { transform: rotate(  0.0deg); }
    10% { transform: rotate(-10.0deg); }
    20% { transform: rotate( 12.0deg); }
    30% { transform: rotate(-10.0deg); }
    40% { transform: rotate(  9.0deg); }
    50% { transform: rotate(  0.0deg); }
    100% { transform: rotate(  0.0deg); }
  }
</style>

<div class="w-full">
  <div class="py-12 content">
    <V class="pb-6 animate" oneWay style="--animate-x: -3rem">
      <h2
        class="flex flex-col m-auto mb-12 text-center -z-10"
        >
        <span
          class="-mb-3 text-5xl leading-none text-gray-300 select-none sm:-mb-8 -z-10 dark:opacity-25 sm:text-8xl dark:text-gray-500 font-handwritten"
          >Home</span
        >
         <span
            class="text-4xl leading-none text-center text-gray-700 sm:text-6xl dark:text-gray-500 font-title"
            >
            Welcome to our catering
            <br class="sm:hidden">
            <span>
              <img src="/images/hand.svg" alt="" class="inline px-2 mx-auto mb-4 h-9 sm:h-11 hand">
            </span>
          </span>
        <span class="w-32 m-auto bg-green-500" style="height: 2px"></span>
    </V>

    <V class="w-full px-4 mx-auto my-6 animate card lg:w-6/10" oneWay style="--animate-x: -0.5rem">
      <div class="animate" style="transition-delay: 400ms; --animate-x: 0; --animate-r-x: -64deg">
        <img src="/images/plate.png" alt="" class="mx-auto -mt-12 w-6/10 lg:w-2/10" style="">
      </div>
      <p class="mt-6 mb-6 text-lg text-2xl leading-none text-gray-500 sm:text-xl">
      With the <strong>Seattle Corporate Catering</strong> website we have made it easier and quicker for our  corporate catering clients to place and track their event orders.  If you are planning a large confersiness meeting, ence or just a meal for a regularily scheduled business meeting, treat your attendees to great food and flavor.  SCC will confirm your online order and guarantee the success of your important event.
      </p>
      <div class="flex -mx-2">
        <a class="w-1/2 mx-2 btn" href="/order">Order now</a>
        <button class="w-1/2 mx-2 btn">View cart</button>
      </div>
    </V>
  </div>

  <!--button class="snipcart-add-item"
    data-item-id="starry-night"
    data-item-price="79.99"
    data-item-url="/paintings/starry-night"
    data-item-description="High-quality replica of The Starry Night by the Dutch post-impressionist painter Vincent van Gogh."
    data-item-image="/assets/images/starry-night.jpg"
    data-item-name="The Starry Night"
    data-item-quantity=3>
    Add to cart
  </button-->
</div>
