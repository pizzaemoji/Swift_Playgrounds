//Chapter 2 — Functions

//Baby's first func

//Composing a New Behavior

moveForward()
moveForward()
moveForward()
turnLeft()
turnLeft()
turnLeft()
moveForward()
moveForward()
moveForward()
collectGem()

//Creating a New Function

func turnRight() {
	turnLeft()
	turnLeft()
	turnLeft()
}

moveForward()
turnLeft()
moveForward()
turnRight()
moveForward()
turnRight()
moveForward()
turnRight()
moveForward()
turnLeft()
moveForward()
toggleSwitch()

//Collect, Toggle, Repeat

func walkAround() {
	moveForward()
    collectGem()
    moveForward()
    toggleSwitch()
    moveForward()
}

walkAround()
turnLeft()
walkAround()
moveForward()
turnLeft()
walkAround()
turnLeft()
walkAround()

//Across the Board

func getThree() {
	collectGem()
    moveForward()
    collectGem()
    moveForward()
    collectGem()
}

getThree()
turnRight()
moveForward()
turnRight()
getThree()
turnLeft()
moveForward()
turnLeft()
getThree()

//Nesting Patterns

func turnAround() {
	turnLeft()
    turnLeft()
}

func solveStair() {
	moveForward()
    collectGem()
    turnAround()
    moveForward()
    turnLeft()
}

solveStair()
solveStair()
solveStair()
solveStair()

//Slotted Stairways

func collectGemTurnAround() {
	moveForward()
    moveForward()
    collectGem()
    turnLeft()
    turnLeft()
    moveForward()
    moveForward()
}

func solveRow() {
	collectGemTurnAround()
    collectGemTurnAround()
    turnRight()
    moveForward()
    turnLeft()
}

solveRow()
solveRow()
solveRow()

//Treasure Hunt

func turnAround() {
    turnLeft()
    turnLeft()
}

func twoStep() {
    moveForward()
    moveForward()
}

func shortStep() {
    twoStep()
    toggleSwitch()
    turnAround()
    twoStep()
    turnRight()
}

func longStep() {
    twoStep()
    toggleSwitch()
    twoStep()
    toggleSwitch()
    turnAround()
    twoStep()
    twoStep()
    turnRight()
}

shortStep()
longStep()
shortStep()
longStep()