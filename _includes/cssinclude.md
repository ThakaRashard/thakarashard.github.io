
<style>
  @import url('https://fonts.googleapis.com/css2?family=Caveat:wght@400;700&family=Roboto+Mono:ital,wght@0,200;0,400;0,700;1,200;1,400;1,700&family=Silkscreen:wght@400;700&family=Trade+Winds&display=swap');



body {
  background-color: lightblue;
  font-family: "Space Mono", monospace;
}

  .includedemo1 {

    display: flex;
    
    justify-content: space-between;  
    /* flex-flow: wrap-reverse; */  
    flex-wrap: wrap-reverse; 
    align-content: stretch;
    background-color: #bbdefb;
    height: 40vh;
    padding: 15px;
    gap: 5px;

  }

  .includedemo1 > div{
    background: #ffecb3;
    border: 3px solid #ffcc80;
    border-radius: 5px;
    padding: 8px;
  }


  .item2 { 
    /* flex:1 1 auto; */
    flex-grow:1;
  }
			

</style>
<div class="includedemo1">
   
    <div class="item1">item 1</div>
    <div class="item2"><iframe width=100% height="315" src="https://www.youtube.com/embed/RF87aqqmf4Q?si=qdNeQpc97fjSclz_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></div>
    <div class="item3">item 3</div>

</div>
<div class="includedemo1">
   
    <div class="item1">item 1</div>
    <div class="item2">{{ include.content }}</div>
    <div class="item3">item 3</div>

</div>