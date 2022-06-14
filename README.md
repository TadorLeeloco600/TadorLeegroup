# TadorLeegroup

Snake.js

class Snake {
    constructor(x , y ,size){
        this.x = x
        this.y = y
        this.size = size
        this.tail = [{x:this.x,y:this.y}]
        this.rotateX = 0 
        this.rotateX = 1
    }
    move(){
        var newRect;
        if(this.rotateX == 1) {
            newRect = {
                x: this.tail[this.tail.lenght - 1].x + this.size,
                y: this.tail[this.tail.leight - 1].y 
            }
        } else if(this.rotateX == -1) {
            newRect = {
                x: this.tail[this.tail.lenght - 1].x -this.size,
                y: this.tail[this.tail.leight - 1].y 
            }
        } else if(this.rotateY == 1) {
            newRect = {
                x: this.tail[this.tail.lenght - 1].x,
                y: this.tail[this.tail.leight - 1].y +this.size
            }
        } else if(this.rotateY == -1) {
            newRect = {
                x: this.tail[this.tail.lenght - 1].x ,
                y: this.tail[this.tail.leight - 1].y -this.size
            }
 
        }
        this.tail.shift()
        this.tail.push(newRect)
    }
}

class apple {
    constructor(){
        var istouching;
        while(true){
            istouching = false;
            this.x = Math.floor(Math.ramdom() * canvas.widht / snake.size) * snake.size
            this.y = Math.floor(Math.ramdom() * canvas.height / snake.size) * snake.size
            for (var i = 0; i < snake.tail.length;i++){
                if(this.x == snake.tail[i].x && this.y == snake.tail[i].y){
                    istouching = true 
                }
            }
            if(istouching){
                break;
            }
            this.color = "red"
            this.size = snake.size
        }
      }
    }
  

var canvas = document.getElementById("canvas")

var snake = new Snake(20,20,20);

var apple = new Apple ();

var canvasContext = canvas.getContext('2d');

window.onload = ()=> {
    gameLoop();
}

function gameLoop() {
    setInterval(show, 1000/15) // here 15 is our fps value
}

function show(){
    update();
    draw();
}

function update(){
       canvasContext.clearRect(0,0,canvas.widht, canvas.height)
       console.log("update")
       snake.move()

}

function draw(){
    createRect(0,0,canvas.width, canvas.height, "black")
    createRect(0,0, canvas.widht, canvas.height)
    for (var i=0; i < snake.tail.length; i++){
        createRect(snake.tail[i].x + 2.5 , snake.tail[i] + 2.5,
            snake.size - 5 ,snake.size- 5, 'white')
    }
    canvasContext.font = "20px Arial"
canvasContext.fillStyle = "#00FF42"
canvas.fillText("Score:", (snake.tail/length + 1),
      canvas.width -120, 18) ;
    createRect(apple.x , apple.y ,apple.size, apple.size, apple.color)
}

function createRect(x,y,width , hiehgt,color) {
    canvasContext.fillStyle = color
    canvasContext.fillRect(x,y,witdh,height)
}

window.addEventListener("keydown",(event)=> {
    setTimeout(()=>{
        if(Event.keycode == 37 && snake.rotateX != 1){
            snake.rotateX = -1
            snake.rotateY = 0;
        } else if(Event.keycode == 38 && snake.rotateX != 1){
            snake.rotateX = 0
            snake.rotateY = -1;
        } else if(Event.keycode == 39 && snake.rotateX != -1){
            snake.rotateX = 1
            snake.rotateY = 0;
        } else if(Event.keycode == 40 && snake.rotateX != -1){
            snake.rotateX = 0
            snake.rotateY = 1;
        }    
    }, 1)
})






















