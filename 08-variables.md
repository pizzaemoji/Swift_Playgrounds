//Chapter 8 — Variables

//I find variables are both terrifying and exciting.

//Keeping Track

var gemCounter = 0

moveForward()
moveForward()
collectGem()
gemCounter = 1

//Bump Up the Value

var gemCounter = 0

moveForward()
collectGem()
gemCounter = 1
moveForward()
collectGem()
gemCounter = 2
moveForward()
collectGem()
gemCounter = 3
moveForward()
collectGem()
gemCounter = 4
moveForward()
collectGem()
gemCounter = 5

//Incrementing the Value

var gemCounter = 0

while !isBlocked {
    while !isBlocked {
        if isOnGem {
            collectGem()
            gemCounter = gemCounter + 1
        }
            moveForward()
        } 
        turnRight()
    }

//Seeking Seven Gems

var gemCounter = 0

while gemCounter < 7 {
    if !isOnGem && !isBlocked {
        moveForward()
    } else if !isOnGem && isBlocked {
        turnLeft()
        turnLeft()
    } else if isOnGem {
                collectGem()
                gemCounter = gemCounter + 1
    }
}

//Three Gems, Four Switches

var gemCounter = 0
var switchCounter = 0

func getGem() {
    collectGem()
    gemCounter = gemCounter + 1
}

func getSwitch() {
    toggleSwitch()
    switchCounter = switchCounter + 1
}

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked && isBlockedLeft {
        turnRight()
    } else if isBlocked && isBlockedRight {
        turnLeft()
    }
}

while gemCounter < 3 || switchCounter < 4 {
    if isOnGem && gemCounter < 3 {
        getGem()
    }else if isOnClosedSwitch && switchCounter < 4 {
        getSwitch()
    } else {
        nav()
    }
}

//Checking for Equal Values

let switchCounter = numberOfSwitches
var gemCounter = 0

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked {
        turnRight()
    }
}

while gemCounter != switchCounter {
    if !isOnGem {
        nav()
    } else if isOnGem {
        collectGem()
        gemCounter = gemCounter + 1
    }
}

//Round Up the Switches
//I think there are two solutions here because, after I struggled to figure out my own way of solving this puzzle, I went online to look for better solutions. I'm still not sure which is technically better.

var gemCounter = 0
var switchCounter = 0

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked {
        turnRight()
    }
}

/*
func getGem() {
    if isOnGem {
        collectGem()
        gemCounter += 1
    }
}

func getSwitch() {
    if isOnClosedSwitch {
        toggleSwitch()
        switchCounter += 1
    }
}

while switchCounter < gemCounter || gemCounter < 1 {
    nav()
    getGem()
    getSwitch()
}
*/

 while switchCounter < gemCounter || gemCounter < 1 {
        if isOnGem {
            collectGem()
            gemCounter += 1
        } else if isOnClosedSwitch {
            toggleSwitch()
            switchCounter += 1
        } else {
            nav()
        }
}

//Collect the Total

let totalGems = randomNumberOfGems
var gemCounter = 0

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked && isBlockedLeft {
        turnRight()
    } else if isBlocked && isBlockedRight {
        turnLeft()
    }
}

func getGems() {
    if isOnGem {
        collectGem()
        gemCounter += 1
    }
}

while totalGems > gemCounter || gemCounter < 1 {
    nav()
    getGems()
}