<div class="loading">
     <svg class="loader" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 340 340">
     <circle cx="170" cy="170" r="160" stroke="#C24924"/>
     <circle cx="170" cy="170" r="135" stroke="#404041"/>
     <circle cx="170" cy="170" r="110" stroke="#C24924"/>
     <circle cx="170" cy="170" r="85" stroke="#404041"/>
  </svg>
</div>

<style>
.loader {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: -1;
    min-height: 100vh;
    min-width: 10em;
    background-color: #ededed;
}

.loader {
  max-width: 2rem;
  width: 100%;
  height: auto;
  stroke-linecap: round;
}

circle {
  fill: none;
  stroke-width: 3.5;
  -webkit-animation-name: preloader;
          animation-name: preloader;
  -webkit-animation-duration: 3s;
          animation-duration: 3s;
  -webkit-animation-iteration-count: infinite;
          animation-iteration-count: infinite;
  -webkit-animation-timing-function: ease-in-out;
          animation-timing-function: ease-in-out;
  transform-origin: 170px 170px;
  will-change: transform;
}
circle:nth-of-type(1) {
  stroke-dasharray: 550px;
}
circle:nth-of-type(2) {
  stroke-dasharray: 500px;
}
circle:nth-of-type(3) {
  stroke-dasharray: 450px;
}
circle:nth-of-type(4) {
  stroke-dasharray: 300px;
}
circle:nth-of-type(1) {
  -webkit-animation-delay: -0.15s;
          animation-delay: -0.15s;
}
circle:nth-of-type(2) {
  -webkit-animation-delay: -0.3s;
          animation-delay: -0.3s;
}
circle:nth-of-type(3) {
  -webkit-animation-delay: -0.45s;
          animation-delay: -0.45s;
}
circle:nth-of-type(4) {
  -webkit-animation-delay: -0.6s;
          animation-delay: -0.6s;
}

@-webkit-keyframes preloader {
  50% {
    transform: rotate(360deg);
  }
}

@keyframes preloader {
  50% {
    transform: rotate(360deg);
  }
}
</style>