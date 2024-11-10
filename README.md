<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  
    <link rel="stylesheet" href="style.css">
</head>
<body>
   <h1>Sketch Me Up</h1>
   <div class="instructions">Hold shift and drag to darken squares, or hold Ctrl to lighten!<button id="erase">New Grid</button></div>
   <div id="sketch-boxes"></div>
    <script src="script.js"></script>
</body>
</html>
//
//
#sketch-boxes {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    max-width: 1502px;
    border: solid 1px lightslategray;
    
}

.box {
    min-width: 23px;
    min-height: 23px;
    border: solid 1px grey;
    background-color: black;
    opacity: 0;
}

h1 {
    text-align: center;
    margin: 0;
    padding: 0;
}

.instructions {
    text-align: center;
}
//
//
//
let boxesContainer = document.getElementById('sketch-boxes');
let eraseBtn = document.getElementById('erase');

function genBoxes () {
    while (boxesContainer.firstChild) {
        boxesContainer.removeChild(boxesContainer.lastChild)
    }
    let numBoxes = prompt("How many boxes per side?\nAny number lower than 100");
    while (numBoxes > 100) {
        numBoxes = prompt(`Error ${numBoxes} is not a number smaller than 100\nPlease enter a number lower than 100`);
    }
    boxesContainer.style.maxWidth = `${numBoxes*25}px`
    for (let i = 0; i < (Number(numBoxes)*Number(numBoxes)); i++){
        let newBox = document.createElement('div');
        newBox.classList.add('box');
        boxesContainer.appendChild(newBox);
    }
}

function colorBoxes (targetBox) {
    if (targetBox.class = 'box' && targetBox.shiftKey == true) {
        let darken = Number(targetBox.target.style.opacity)
        if (darken < 1){
        targetBox.target.style.opacity = (darken + .1) }
    } else if (targetBox.class = 'box' && targetBox.ctrlKey == true){
        let lighten = Number(targetBox.target.style.opacity);
        if (lighten > 0) {
        targetBox.target.style.opacity = (lighten - .1) }
    }
    
}

genBoxes();
boxesContainer.addEventListener('mouseover', colorBoxes);
eraseBtn.addEventListener('click', genBoxes);
