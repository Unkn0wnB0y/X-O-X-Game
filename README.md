# X-O-X-Game
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XOX Game</title>
    <style>
      * {
    margin: 0;
    padding: 0;
}
h1{
    padding: 40px;
}
body {
    background-color:  #11403f;
    text-align: center;
}
.container {
    height: 70vmin;
    display: flex;
    text-align: center;
    justify-content: center;
}
.game {
    height: 60vmin;
    width: 60vmin;
    display: flex;
    flex-wrap: wrap;
    text-align: center;
    justify-content: center;
    gap: 2%;
}
.box {
    height: 17vmin;
    width: 17vmin;
    border-radius: 1rem;
    border: none;
    box-shadow: 0 0 1rem  rgba(0,0,0.5);
    font-size: 8vmin;
    color:#F05D0E ;
    background-color: #ffff07;

}
#reset-btn{
    padding: 1rem;
    font-size: 1.2rem;
    background-color: #191913;
    color: #fff;
    border-radius: 1rem;
    border: none;
}
#newgame-btn{
    padding: 1rem;
    font-size: 1.2rem;
    background-color: #191913;
    color: #fff;
    border-radius: 1rem;
    border: none;
}
#msg {
    color: #ffffc7;
    font-size: 5vmin;
}
.msg-container {
    height: 100vmin;
    display: flex;
    justify-content: center; 
    align-items: center;
    flex-direction: column;
    gap: 4 rem;
}
.hide {
    display: none;
}
      </style>
</head>
<body>
     <div class="msg-container hide">
        <p id="msg">Winner</p>
        <button id="newgame-btn">New Game</button>
    </div>
    <main>
    <h1>Tic Tac Toe</h1>
    <div class="container">
    <div class="game">
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
        <button class="box"></button>
    </div>
</div>
<button id="reset-btn">Reset Game</button>
      <script>
        let boxes = document.querySelectorAll(".box");
let resetbtn =document.querySelector("#reset-btn");
let newGameBtn = document.querySelector("#newgame-btn");
let msgContainer = document.querySelector(".msg-container");
let msg = document.querySelector("#msg");
let turnO = true; //playerX,playerO
const winPatterns =[
    [0,1,2],
    [0,3,6],
    [0,4,8],
    [1,4,7],
    [2,5,8],
    [2,4,6],
    [3,4,5],
    [6,7,8],
];
const resetGame = () => {
turnO = true;
enableBoxes ();
msgContainer.classList.add ("hide");
}
boxes.forEach((box) => {
box.addEventListener("click",() =>{
    if(turnO) {
    box.innerText ="O";
     turnO=false;
    } else {
        box.innerText ="X";
        turnO = true;
    }
    box.disabled = true ;
    checkWinner();
});
});
const disableBoxes = () => {
    for (let box of boxes) {
        box.disabled = true;
    }
};
const enableBoxes = () => {
    for(let box of boxes) {
        box.disabled = false;
        box.innerText = "";
    }
};
const showWinner = (winner) => {
    msg.innerText = `Congratulations, Winner is ${winner}`;
    msgContainer.classList.remove("hide");
    disableBoxes();
};
const checkWinner = () => {
    for (pattern of winPatterns) {
       
        let pos1val = boxes[pattern[0]].innerText;
        let pos2val = boxes[pattern[1]].innerText;
        let pos3val = boxes[pattern[2]].innerText;
        if (pos1val != "" && pos2val != "" && pos3val != ""){
            if (pos1val == pos2val && pos2val==pos3val){
                showWinner(pos1val);
            }
        }
    }
};
newGameBtn.addEventListener("click",resetGame);
resetbtn.addEventListener("click",resetGame);
      </script>
</body>
</html>
