//Chapter 5 — Logical Operators

//For the first time in my life, I feel like I'm finally understanding some of these programming concepts. Very exciting.

//Using the NOT Operator

for i in 1 ... 4 {
    moveForward()
    if !isOnGem {
        turnLeft()
        moveForward()
        moveForward()
        collectGem()
        turnRight()
        turnRight()
        moveForward()
        moveForward()
        turnLeft()
    } else if isOnGem {
        collectGem()
    }
}

//Spiral of NOT

for i in 1 ... 16 {
    if !isBlocked {
        moveForward()
    } else if isBlocked {
        turnLeft()
    }
}
toggleSwitch()

//Checking This AND That

for i in 1 ... 7 {
    moveForward()
    if isBlockedLeft && isOnGem {
        collectGem()
        turnRight()
        moveForward()
        moveForward()
        toggleSwitch()
        turnLeft()
        turnLeft()
        moveForward()
        moveForward()
        turnRight()
    } else if isOnGem {
    	collectGem()
    }    
}

//Checking This OR That

for i in 1 ... 12 {
    if isBlockedLeft || isBlocked {
        turnRight()
        moveForward()
    } else {
        moveForward()
    }
}
collectGem()

//Logical Labyrinth
//I guess technically this works, but it probably wasn't what they had in mind.

for i in 1 ... 8 {
    moveForward()
    if isOnGem && isOnClosedSwitch {
        toggleSwitch()
        collectGem()
        turnRight()
        moveForward()
        moveForward()
        collectGem()
        turnLeft()
        turnLeft()
        moveForward()
        moveForward()
        turnRight()
    } else if isOnClosedSwitch {
        toggleSwitch()
        turnLeft()
    } else if isOnGem {
        collectGem()
    }
}