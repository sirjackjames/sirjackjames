#_BLOCK_ .words[data-effect="typewriter"]::after {
  content:'|';
  display: inline;
  animation: changing-text-typewritter-carret-blink 1s infinite;
}
@keyframes changing-text-typewritter-carret-blink {
  0% {opacity: 1;}
  50% {opacity: 0;}
  100% {opacity: 1;}
}


#_BLOCK_ .words[data-effect="fallingLetters"],
#_BLOCK_ .words[data-effect="opacity"],
#_BLOCK_ .words[data-effect="slidingTextDown"],
#_BLOCK_ .words[data-effect="slidingTextUp"],
#_BLOCK_ .words[data-effect="rotationX"],
#_BLOCK_ .words[data-effect="rotationY"] {
  display:inline-grid;
  grid-template-columns:auto;
  grid-template-rows:auto;
  justify-items:center;
  perspective-origin: center center;
  perspective: 1000px;
  overflow:hidden;
  & > span {
    grid-row: 1 / 1;
    grid-column: 1 / 1;
    text-align:center;
    transition:all {{ 'transition' | css_var }};
  }
}


#_BLOCK_ .words[data-effect="fallingLetters"] span {
  &>span {
    display:inline-block;
    opacity:0;
    transform:translateY(-50%);
    transition:all {{ 'transition' | css_var }};
  }
  &[data-status="current"]>span {
    transform:translateY(0%);
    opacity:1;
  }
  &[data-status="prev"]>span {
    transform:translateY(50%);
  }
}

#_BLOCK_ .words[data-effect="opacity"] span {
  opacity:0;
  &[data-status="current"] {
    opacity:1;
  }
}
#_BLOCK_ .words[data-effect="slidingTextDown"] span {
  opacity:0;
  transform:translateY(-50%);
  &[data-status="current"] {
    transform:translateY(0%);
    transition-delay: calc({{ 'transition' | css_var }} / 3);
    opacity:1;
  }
  &[data-status="prev"] {
    transform:translateY(50%);
  }
}
#_BLOCK_ .words[data-effect="slidingTextUp"] span {
  opacity:0;
  transform:translateY(50%);
  &[data-status="current"] {
    transform:translateY(0%);
    transition-delay: calc({{ 'transition' | css_var }} / 3);
    opacity:1;
  }
  &[data-status="prev"] {
    transform:translateY(-50%);
  }
}

#_BLOCK_ .words[data-effect="rotationX"] span {
  opacity:0;
  transform:rotateX(90deg);
  &[data-status="current"] {
    transform:rotateX(0deg);
    transition-delay: calc({{ 'transition' | css_var }} / 2);
    opacity:1;
  }
  &[data-status="prev"] {
    transform:rotateX(-90deg);
  }
}

#_BLOCK_ .words[data-effect="rotationY"] span {
  opacity:0;
  transform:rotateY(90deg);
  &[data-status="current"] {
    transform:rotateY(0deg);
    transition-delay: calc({{ 'transition' | css_var }} / 2);
    opacity:1;
  }
  &[data-status="prev"] {
    transform:rotateY(-90deg);
  }
}
