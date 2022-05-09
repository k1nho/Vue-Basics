<script setup>
import ClickCounter from "./components/ClickCounter.vue";

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
        <div style="display: flex; margin-bottom: 10px">
          <!-- Normal method with just native event-->
          <button id="counter-btn" @click="printCount">Count</button>
          <!-- Inline method handlers to pass params can be done as follows-->
          <button @click="say('hello world')">Hello World</button>
          <!-- Inline method with both native event and a param-->
          <button
            name="param"
            @click="messageAndEvent('Inline handler with event', $event)"
          >
            Msg and Param
          </button>
        </div>
      </div>
      <hr />
      <div>
        <h1 class="title">Form Input bindings</h1>
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
