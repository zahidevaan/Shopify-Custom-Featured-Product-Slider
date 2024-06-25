# Shopify-Custom-Featured-Product-Slider
Shopify Custom Featured Product Slider Source Code

# Add this code in to your theme.liquid file under <head> </head> Tag


    <!-- jQuery CDN Start here -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
    <!-- jQuery CDN End here -->

    <!-- Rimixicon CDN start here -->
    <link href="https://cdn.jsdelivr.net/npm/remixicon@4.3.0/fonts/remixicon.css" rel="stylesheet"/>
    <!-- Rimixicon CDN end here -->

    <!-- Slick slider CDN Start here -->
        <!-- Add the slick-theme.css if you want default styling -->
        <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.css"/>
        <!-- Add the slick-theme.css if you want default styling -->
        <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick-theme.css"/>

        <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.min.js"></script>
    <!-- Slick slider CDN End here -->

    
# Create a New section called "New Featured Products Slider" liquid file and add this below code in to this file 


<section class="section__wrapper">

    <div class="slider__contents__wrapper">

        <div class="slider__title__content">
            <h2 class="slider__title">{{ section.settings.heading }}</h2>
        </div>
        <!-- main slider start here -->
        <div class="main__slider">

{% for product in section.settings.products %}
            <!-- Single Slide start here -->
            <div class="single__slide">
                <div class="slide__contents">
                    <img src="{{ product.featured_image | image_url }}" width="" height="" alt="">
                </div>

                <div class="slide___reviews">
                    <i class="ri-star-fill"></i>
                    <i class="ri-star-fill"></i>
                    <i class="ri-star-fill"></i>
                    <i class="ri-star-fill"></i>
                    <i class="ri-star-fill"></i>
                    <span>125(Reviews)</span>
                </div>

                <div class="slide__info">
                    <h2 class="slide__title">{{ product.title }} </h2>
                    <p class="slider__price">{{ product.price | money }}</p>
                </div>
            </div>
            <!-- Single Slide end here -->
        {% endfor %}  

        </div>
        <!-- main slider end here -->
    </div>
</section>



{% schema %}
  {
    "name": "New Product Slider",
    "settings": [
      {
        "type": "text",
        "id": "heading",
        "label": "Slider Heading",
        "default": "Featured Products"
      },
      {
        "type": "product_list",
        "id": "products",
        "label": "Select Your Products"
      }
    ],
    "presets": [
      {
        "name": "New Product Slider"
      }
    ]
  }
{% endschema %}

<script>
$('.main__slider').slick({
  draggable: true,
  dots: true,
  infinite: true,
  speed: 300,
  slidesToShow: 4,
  slidesToScroll: 1,
  autoplay: true,
  responsive: [
    {
      breakpoint: 1024,
      settings: {
        slidesToShow: 3,
        slidesToScroll: 1,
        infinite: true,
        dots: true
      }
    },
    {
      breakpoint: 600,
      settings: {
        slidesToShow: 1,
        slidesToScroll: 1
      }
    },
    {
      breakpoint: 480,
      settings: {
        slidesToShow: 1,
        slidesToScroll: 1
      }
    }
  ]
});
</script>
