<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissor Game</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Rock Paper Scissor Game</h1>
    <div class="choices">
        <div class="choice" id="paper">
            <img src="c:\Users\LENOVO\Downloads\paper.png" alt="paper">
            </div>
            <div class="choice" id="rock">
                <img src="c:\Users\LENOVO\Downloads\rock.png" alt="rock">
            </div>
            <div class="choice" id="scissors">
            <img src="c:\Users\LENOVO\Downloads\scissors.png" alt="scissors">
        </div>
    </div>
    <div class="score-board">
        <div class="score">
            <p id="user-score">0</p>
            <p>You</p>
        </div>
        <div class="score">
            <p id="comp-score">0</p>
            <p>Computer</p>
        </div>
    </div>
    <div class="msg-container">
        <p id="msg">Play your Move</p>
    </div>
    <script src="app.js"></script>
</body>
</html>

css
*{
    margin:0;
    padding:0;
    text-align:center;
}
h1{
    background-color:#081b31;
    color:#fff;
    height:5rem;
    line-height:5rem; /*this is for center the text*/
}
.choice{
    height:165px;
    width:165px;
}
.choice:hover{
    opacity:0.5;
    cursor:pointer;
}
img{
    height:150px;
    width:150px;
    object-fit:cover;
    border-radius:50%;
}
.choices{
    display:flex;
    justify-content:center;
    align-items:center;
    gap:3rem;
    margin-top:5rem;
}
.score-board{
    display:flex;
    justify-content: center;
    align-items:center;
    font-size:2rem;
    margin-top:3rem;
    gap:5rem;
}
#user-score, #comp-score
{
    font-size:4rem;
}
#msg{
    margin-top:5rem;
    background-color: #081b31;
    color:#fff;
    height:5rem;
    line-height:5rem;
    display:inline;
    padding:1rem;
    border-radius:1rem;
}

let userScore=0;
let comScore=0;
const  msg=document.querySelector("#msg");
let userScorePara=document.querySelector("#user-score");
let compScorePara=document.querySelector("#comp-score");

const choices=document.querySelectorAll(".choice");
const drawGame = ()=>
{
    console.log("Game is draw");
    msg.innertext="Game was Draw";
}
const showWinner=(userWin)=>
{
    if(userWin){
        console.log("you Win");
        msg.innertext="you Win";
        userScorePara++;
    }else{
        console.log("you lose");
        msg.innertext="Computer win";
        compScorePara++;
    }
}


const genCompChoice=()=>{
    const options=["rock","paper","scissors"];
    const randIndx=Math.floor(Math.random()*3);
    return options[randIndx];// options re jaha string achi seita ku index value hisab re bahar kariba pai emt lekha hela reutrn kariba vlaue;
}

const playGame = (userChoice) =>{
    //console.log("choice was clicked", userChoice);
    //lets write computer generate code
    const compChoice=genCompChoice();
    console.log("choice was clicked", compChoice);
    if(userChoice===compChoice){
        drawGame();
    }
    else{
         let userWin=true;
         if(userChoice==="rock"){
            userWin= compChoice==="paper" ? false :true;// if else statement in one line
         }else if(userChoice==="paper"){
            userWin=compChoice==="scissors" ? false: true;
         }else{
               userWin= compChoice==="rock" ? false: true;
         }
    }
};

choices.forEach((choice) => {
    //console.log(choice);
    choice.addEventListener("click",() =>{
    const userChoice=choice.getAttribute("id");

        playGame();
    });
});
