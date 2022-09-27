<template>
  <p>
    <span>
      <slot></slot>
    </span>
  </p>
</template>

<style scoped>
p {
  text-transform: uppercase;
  letter-spacing: 0.2em;
  border: 4px double rgba(255, 255, 255, 0.25);
  border-width: 4px 0;
  padding: 1.5em 0em;
  
  
}

span {
  font: 700 4em/1 "Oswald", sans-serif;
  font-size: 2.5rem;
  letter-spacing: 0;
  padding: 0.25em 0 0.325em;
  text-shadow: 0 0 80px rgba(255, 255, 255, 0.5);

  /* Clip Background Image */

  background: url(https://i.ibb.co/RDTnNrT/animated-text-fill.png) repeat-y;
  -webkit-background-clip: text;
  background-clip: text;

  /* Animate Background Image */

  -webkit-text-fill-color: transparent;
  -webkit-animation: aitf 80s linear infinite;

  /* Activate hardware acceleration for smoother animations */

  -webkit-transform: translate3d(0, 0, 0);
  -webkit-backface-visibility: hidden;
}

/* Animate Background Image */

@-webkit-keyframes aitf {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}
</style>
