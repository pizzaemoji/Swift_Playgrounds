//Chapter 3 — For Loops

//Found loops to be fairly easy; I don't think the functions in this section are the focus.

//Using Loops

for i in 1 ... 5 {
	moveForward()
    moveForward()
    collectGem()
    moveForward()
}

//Looping All the Sides

for i in 1 ... 4 {
    moveForward()
    collectGem()
    moveForward()
    moveForward()
    moveForward()
    turnRight()
}

//To the Edge and Back

for i in 1 ... 4 {
    moveForward()
    moveForward()
    toggleSwitch()
    turnLeft()
    turnLeft()
    moveForward()
    moveForward()
    turnLeft()    
}

//Loop Jumper

for i in 1 ... 5 {
    moveForward()
    turnLeft()
    moveForward()
    moveForward()
    collectGem()
    turnRight()
}

//Branch Out
//As a new "programmer" I'm not sure if my "letsAGo" function is better kept as a function or if it should just be in the loop. I do like that the loop is clean, but it does seem to add some complexity to the list of functions. I feel like functions should be cleaner. Maybe someday I'll look back on this and cringe.

func sevenSteps() {
    moveForward()
    moveForward()
    moveForward()
    moveForward()
    moveForward()
    moveForward()
    moveForward()
}

func turnAround() {
    turnLeft()
    turnLeft()
}

func letsAGo() {
    moveForward()
    moveForward()
    turnRight()
    sevenSteps()
    toggleSwitch()
    turnAround()
    sevenSteps()
    turnRight()
}

for i in 1 ... 3 {
    letsAGo()
}

//Gem Farm
//So again, here are some complex looking functions, but the instructions on the page state, "You'll need to identify the patterns for gem collection and switch activation. Then you'll write a function for each pattern and figure out how many times you'll need to call those functions using loops." I think, conceptually at least, I followed the instructions.

func collectTwo() {
    turnRight()
    moveForward()
    collectGem()
    moveForward()
    collectGem()
    turnAround()
    moveForward()
    moveForward()
}

func switchTwo() {
    moveForward()
    toggleSwitch()
    moveForward()
    toggleSwitch()
    turnAround()
    moveForward()
    moveForward()
    turnLeft()
}

func turnAround() {
    turnLeft()
    turnLeft()
}

for i in 1 ... 3 {
    collectTwo()
    switchTwo()
    moveForward()
}

//Four Stash Sweep
//The function is called "collectT" because the gems are in a T-shape.

func turnAround() {
    turnLeft()
    turnLeft()
}

func collectT() {
    moveForward()
    collectGem()
    moveForward()
    collectGem()
    turnAround()
    moveForward()
    turnRight()
    moveForward()
    collectGem()
    turnAround()
    moveForward()
    moveForward()
    collectGem()
    moveForward()
}

for i in 1 ... 4 {
    collectT()
    
}