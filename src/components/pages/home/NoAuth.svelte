<script>
  import Carousel from '../../carousel/Carousel.svelte'
  import V from '../../IntersectingViewport.svelte'

  import Intro from './Intro.svelte'

  const slides = [
    {
      centered: true,
      img: '/images/logo.webp',
      content: 'Fresh and express\ncorporate catering',
      bg: 'url(/images/bg.jpg)',
    }
  ]
</script>

<style>
  .heart {
    position: relative;
    display: inline;
    animation: pulse 1s ease infinite;
  }

  @keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.3); }
    100% { transform: scale(1); }
  }
</style>

<div class="w-full">
  <Carousel height="95vh" slides={slides} waves/>
  <div class="content">
    <Intro/>
    <V class="w-full px-4 mx-auto my-6 animate card lg:w-6/10" oneWay style="--animate-x: -0.5rem">
      <div class="animate" style="transition-delay: 400ms; --animate-x: 0; --animate-r-x: -64deg">
        <img src="/images/plate.png" alt="" class="mx-auto -mt-12 w-6/10 lg:w-2/10" style="">
      </div>
      <p class="mt-6 mb-6 text-lg text-2xl leading-none text-gray-500 sm:text-xl">
      With the <strong>Seattle Corporate Catering</strong> website we have made it easier and quicker for our  corporate catering clients to place and track their event orders.  If you are planning a large confersiness meeting, ence or just a meal for a regularily scheduled business meeting, treat your attendees to great food and flavor.  SCC will confirm your online order and guarantee the success of your important event.
      </p>
      <div class="flex -mx-2">
        <a href="/request-estimate" class="w-1/2 mx-2 btn">Request estimate</a>
        <a href="/login" class="w-1/2 mx-2 btn">Log in</a>
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
