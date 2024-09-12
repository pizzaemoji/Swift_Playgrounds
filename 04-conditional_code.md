//Chapter 4 — Conditional Code

//The introduction to else if — now it feels like I'm coding!

//Checking for Switches

moveForward()
for i in 1 ... 3 {
    moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    }
}

//Using else if

for i in 1 ... 2 {
    moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    } else if isOnGem {
        collectGem()
    }
}

//Looping Conditional Code

for i in 1 ... 12 {
	moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    } else if isOnGem {
        collectGem()
    }
}

//Conditional Climb

for i in 1 ... 16 {
    if isOnGem {
        turnLeft()
        collectGem()
    } else {
        moveForward()
    }
}

//Defining Smarter Functions
//This looks like I was rushing. Could probably have been cleaner.

func collectOrToggle() {
moveForward()
    if isOnGem {
        collectGem()
    } else if isOnClosedSwitch {
        toggleSwitch()
	}
}

func walkTheLine() {
    moveForward()
    collectOrToggle()
    moveForward()
    collectOrToggle()
}

walkTheLine()
turnLeft()
moveForward()
moveForward()
turnLeft()
walkTheLine()
turnRight()
moveForward()
turnRight()
walkTheLine()

//Boxed In
//Yeah, that move/turn/move is a bit of a cheat to get the character moving in the loop.

func collectOrToggle() {
    if isOnGem {
        collectGem()
    } else if isOnClosedSwitch {
        toggleSwitch()
    }   
}

moveForward()
turnRight()
moveForward()

for i in 1 ... 4 {
    turnRight()
    collectOrToggle()
    moveForward()
    collectOrToggle()
    moveForward()
    collectOrToggle()
}

//Decision Tree

func solveRight() {
    collectGem()
    turnRight()
    stepThree()
    turnLeft()
    moveForward()
    collectGem()
    turnAround()
    moveForward()
    turnRight()
    stepThree()
    turnRight()
}

func solveLeft() {
    turnLeft()
    moveForward()
    collectGem()
    turnAround()
    moveForward()
    turnLeft()
    toggleSwitch()
}

func turnAround() {
    turnLeft()
    turnLeft()
}

func stepThree() {
    moveForward()
    moveForward()
    moveForward()
}

for i in 1 ... 5 {
    moveForward()
    if isOnGem {
        solveRight()
    } else if isOnClosedSwitch {
        solveLeft ()
    }
}