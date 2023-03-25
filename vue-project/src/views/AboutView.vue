<template>
  <div class="about">
    <h1>To Do App</h1>
    <br>
    <p>
      Vue Todos is a CRUD Todo tracking application created to practice Vue 3 by Troy Witonsky.
      <br>
      <br>
      Track your daily task's using this todo tracker with abilities to save, complete, edit & delete todos.
      <br>
      <br>
      Things to add to increase learning: 
    </p>
    <ul class="list">
      <li>using enter as well as clicks for input</li> 
      <li>ability to drag and reorder todos</li>
      <li>animate creation/deletion of todos</li>
      <li>full stack application with the ability to have different lists for different days of tracking todos!</li>
    </ul>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    font-family: Rubik,sans-serif;
    margin: 15px;
    padding: 5px;
    box-sizing: border-box;
  }
}
ul {
  list-style-type: disc;
  padding-left: 2rem;
}



</style>
