<script setup>
import ClickCounter from "./components/ClickCounter.vue";
import InputCheckbox from "./components/InputCheckbox.vue";
import InputRadio from "./components/InputRadio.vue";
import InputSelect from "./components/InputSelect.vue";
import InputText from "./components/InputText.vue";

// We can get the native DOM  element that call the method with e
function printCount(e) {
  if (e) {
    console.log(e.target.id);
  }
}

// Inline handler method that accepts params
function say(msg) {
  console.log(msg);
}

function messageAndEvent(msg, e) {
  if (e) {
    console.log(msg + " " + e.target.name);
  } else {
    console.log("Only message was delivered");
  }
}
</script>

<template>
  <main>
    <div>
      <h1 class="title">
        How to use text interpolation to load Vue instance's data?
      </h1>
      <p>
        We can use text interpolation in Vue by using the mustache syntax "{ { }
        }"
      </p>
    </div>
    <hr />
    <div>
      <h1 class="title">
        How to allow reactivity by binding attributes to Vue instance data ?
      </h1>
      <p>
        Idea here is to use the ":" syntax before the attribute this signifies
        v-bind directive which binds the data to the attribute.
      </p>
      <p>
        We can use the property button to ilustrate the example. The idea here
        is we want to disable the button dynamically so we use Vue's instance
        data that resolves the attribute value.
      </p>
      <hr />
      <div>
        <h1 class="title">Listening to events in Vue</h1>
        <p>
          We can use the v-on directive
          <span style="font-weight: bold"> (@ for shorthand) </span>
          to listen to dom events. In addition, we can do it inline or by
          invoking a method name. It is important to notice that we have access
          to the native DOM element that triggers the event as a parameter to
          the method.
        </p>
        <p style="margin-bottom: 10px">
          We can call methods in an inline handler rather than biding to the
          name directly which allows us to have parameters to pass, instead of
          just the native event
        </p>
        <div style="
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            margin-bottom: 10px;
            gap: 10px;
          ">
          <!-- Normal method with just native event-->
          <button class="button-56" id="counter-btn" @click="printCount">
            Count
          </button>
          <!-- Inline method handlers to pass params can be done as follows-->
          <button class="button-85" @click="say('hello world')">
            Hello World
          </button>
          <!-- Inline method with both native event and a param-->
          <button name="param" @click="messageAndEvent('Inline handler with event', $event)">
            Msg and Param
          </button>
        </div>
        <p style="margin-bottom: 10px;">In addition, we can abstract DOM details away from method logic by using event
          modifiers.
        <ul>
          <li>
            Prevent: same as preventDefault() use to stop browser from reloading on submit.
          </li>
          <li>
            Stop: same as stopPropagation() prevents the propagation of the same event from being called (bubbling to
            parents or capturing children).
          </li>
          <li>
            Self: Only trigger if the event.target is the same as itself and not a child element
          </li>
          <li>
            Passive: Let the default behaviour of the event to happen immediately instead of waiting for the event to
            complete. It is usually good for improving performance on mobile devices.
          </li>
          <li>
            Capture: Usually used when adding the event listener.
          </li>
          <li>
            Once: An event will be triggered at most once.
          </li>
        </ul>
        </p>
        <p>
          The last way of handling events is via <span style="font-weight: bold">keys</span> and <span
            style="font-weight: bold">mouse</span>.
          For keys, we can use @keyup follow by any of these: <span style="font-weight: bold">enter, tab, delete, esc,
            space, up, down, left, right.</span>
          In addition, we can use one of the following modifiers <span style="font-weight:bold"> ctrl, alt, shift,
            meta</span> to respond only when the key is selected in conjunction to any of the aforementioned
          For mouse, we can have <span style="font-weight: bold"> left, right, middle.</span>

        </p>
      </div>
      <hr />
      <div>
        <h1 class="title">Form Input bindings</h1>
        <p>We can do two way binding using <span style="font-weight: bold;">v-model</span> directive. In addition,
          v-model can be used with tags such as textarea and select.</p>
        <hr>
        <InputText />
        <hr>
        <InputCheckbox />
        We can also have a special type of input checkbox in which the value is dynamically binded with <span
          class="bold">:true-value and :false-value</span>
        <hr>
        <div>
          <InputRadio />
        </div>
        <hr>
        <div>
          <InputSelect />
          For select we can also add the attribute multiple and we can have the selection bounded to an array of
          selections.
        </div>
        <hr>
        <div>
          <h2>Special Input Bindings</h2>
          <p>Sometimes we might prefer to have values be dynamically binded rather than statically provided,
            in that case there are many ways in which Vue allow us to have that possibility as it was demonstrated with
            the use of true-value and false-value. Since we can have
            dynamically binded values then we can also allow to have objects as it is the case with the use of select
            input.</p>
        </div>
        <hr>
        <div>
          <h2>Form Input Modifiers</h2>
          <p>Similar to modifiers used for events, we also have modifiers for input forms with three of the most popular ones being: lazy, number, and trim.
            <ul>
              <li>lazy: allows to sync the input after change instead of input.</li>
              <li>number: cast the input automatically to a number type.</li>
              <li>trim: trims whitespace from the input automatically.</li>
            </ul>
          </p>
        </div>
        <hr>
      </div>
      <div>
        <ClickCounter />
      </div>
    </div>
  </main>
</template>

<style>
@import "./assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

.bold {
  font-weight: bold;
}

/* CSS */
.button-56 {
  align-items: center;
  background-color: #42b8e7;
  border: 2px solid #111;
  border-radius: 8px;
  box-sizing: border-box;
  color: #111;
  cursor: pointer;
  display: flex;
  font-family: Inter, sans-serif;
  font-size: 16px;
  height: 48px;
  justify-content: center;
  line-height: 24px;
  max-width: 100%;
  padding: 0 25px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-56:after {
  background-color: #111;
  border-radius: 8px;
  content: "";
  display: block;
  height: 48px;
  left: 0;
  width: 100%;
  position: absolute;
  top: -2px;
  transform: translate(8px, 8px);
  transition: transform 0.2s ease-out;
  z-index: -1;
}

.button-56:hover:after {
  transform: translate(0, 0);
}

.button-56:active {
  background-color: #42b8e7;
  outline: 0;
}

.button-56:hover {
  outline: 0;
}

@media (min-width: 768px) {
  .button-56 {
    padding: 0 40px;
  }
}

/* CSS */
.button-85 {
  padding: 0.6em 2em;
  border: none;
  outline: none;
  color: rgb(255, 255, 255);
  background: #111;
  cursor: pointer;
  position: relative;
  z-index: 0;
  border-radius: 10px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-85:before {
  content: "";
  background: linear-gradient(45deg,
      #ff0000,
      #ff7300,
      #fffb00,
      #48ff00,
      #00ffd5,
      #002bff,
      #7a00ff,
      #ff00c8,
      #ff0000);
  position: absolute;
  top: -2px;
  left: -2px;
  background-size: 400%;
  z-index: -1;
  filter: blur(5px);
  -webkit-filter: blur(5px);
  width: calc(100% + 4px);
  height: calc(100% + 4px);
  animation: glowing-button-85 20s linear infinite;
  transition: opacity 0.3s ease-in-out;
  border-radius: 10px;
}

@keyframes glowing-button-85 {
  0% {
    background-position: 0 0;
  }

  50% {
    background-position: 400% 0;
  }

  100% {
    background-position: 0 0;
  }
}

.button-85:after {
  z-index: -1;
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background: #222;
  left: 0;
  top: 0;
  border-radius: 10px;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  .title {
    font-weight: bold;
  }
}
</style>
