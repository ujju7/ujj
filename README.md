<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Custom Image Slider</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: Arial, sans-serif;
  }

  .slider {
    width: 100%;
    max-width: 100%;
    height: 400px;
    overflow: hidden;
    position: relative;
    margin: auto;
  }

  .slides {
    display: flex;
    width: 500%;
    height: 100%;
    transition: transform 0.5s ease-in-out;
  }

  .slides img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Dots */
  .dots {
    text-align: center;
    position: absolute;
    bottom: 10px;
    width: 100%;
  }

  .dot {
    height: 12px;
    width: 12px;
    margin: 0 5px;
    display: inline-block;
    border-radius: 50%;
    background-color: #bbb;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .active {
    background-color: #717171;
  }
</style>
</head>
<body>

<div class="slider">
  <div class="slides">
    <img src="https://i.imgur.com/xhwIcVA.jpg">
    <img src="https://i.imgur.com/FFGvau5.jpg">
    <img src="https://i.imgur.com/l5PBUlK.jpg">
    <img src="https://i.imgur.com/f8NhlCc.jpg">
    <img src="https://i.imgur.com/bKvAOr2.jpg">
  </div>

  <div class="dots">
    <span class="dot active"></span>
    <span class="dot"></span>
    <span class="dot"></span>
    <span class="dot"></span>
    <span class="dot"></span>
  </div>
</div>

<script>
  const slides = document.querySelector('.slides');
  const dots = document.querySelectorAll('.dot');
  let currentIndex = 0;
  const totalSlides = slides.children.length;

  function showSlide(index) {
    slides.style.transform = `translateX(-${index * 100}%)`;
    dots.forEach(dot => dot.classList.remove('active'));
    dots[index].classList.add('active');
  }

  function nextSlide() {
    currentIndex = (currentIndex + 1) % totalSlides;
    showSlide(currentIndex);
  }

  dots.forEach((dot, i) => {
    dot.addEventListener('click', () => {
      currentIndex = i;
      showSlide(currentIndex);
    });
  });

  showSlide(currentIndex);
  setInterval(nextSlide, 3000); // Auto-slide every 3 seconds
</script>

</body>
</html>
