<script>
    let gridSize = 5;
    let robot = {
      x: 0,
      y: 0,
      direction: 'up' 
    };
  
    function onKeyDown(e) {
      switch(e.keyCode) {
        case 38: // Up arrow
          if (robot.y > 0) robot.y--;
          robot.direction = 'up';
          break;
        case 40: // Down arrow
          if (robot.y < gridSize - 1) robot.y++;
          robot.direction = 'down';
          break;
        case 39: // Right arrow
          if (robot.x < gridSize - 1) robot.x++;
          robot.direction = 'right';
          break;
        case 37: // Left arrow
          if (robot.x > 0) robot.x--;
          robot.direction = 'left';
          break;
      }
    }
  </script>
  
  <h1 class=" text-center p-4">Hello you can move this silly little robot around the gird by using the arrow keys on your keyboard :D</h1>
  <div class="grid m-auto">
    {#each Array(gridSize * gridSize) as _, i}
      <div class:robot={i === robot.y * gridSize + robot.x} class="">
        {#if i === robot.y * gridSize + robot.x}
          <div class={robot.direction}>
            🤖
          </div>
        {/if}
      </div>
    {/each}
  </div>
  
  <style>
    .grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      width: 300px; 
      border: 1px solid #ccc;
    }
  
    .grid div {
      height: 60px;
      border: 1px solid #ccc;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  
    .robot {
      background-color: lightblue;
    }
  
    /* Add styles for different directions */
    .up {
      transform: rotate(0deg); 
    }
  
    .down {
      transform: rotate(180deg); 
    }
  
    .left {
      transform: rotate(-90deg); 
    }
  
    .right {
      transform: rotate(90deg); 
    }
  </style>
  
  <svelte:window on:keydown|preventDefault={onKeyDown} />