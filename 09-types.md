//Chapter 9 — Types

//I'm sorry, but 0 < 0 is not a true statment. Right? I... I have so many questions about the universe now.

//Deactivating a Portal

greenPortal.isActive = false

for i in 1 ... 3 {
    moveForward()
    moveForward()
    moveForward()
    turnLeft()
    moveForward()
    moveForward()
    moveForward()
    toggleSwitch()
    turnLeft()
    turnLeft()
}

//Portal On and Off

var switchCounter = 0
var gemCounter = 0

func portalCheck() {
    if switchCounter == 1 {
        purplePortal.isActive = true
    } else if gemCounter == 3 {
        purplePortal.isActive = false
    }
}

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked {
        turnLeft()
        turnLeft()
    }
}

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

while gemCounter < 7 {
    nav()
    getGem()
    getSwitch()
    portalCheck()
}

//Setting the Right Portal

var gemCounter = 0

bluePortal.isActive = true
pinkPortal.isActive = false

func portalCheck() {
    if gemCounter == 1 {
        bluePortal.isActive = false
    } else if gemCounter == 2 {
        bluePortal.isActive = true
    } else if gemCounter == 3 {
        pinkPortal.isActive = true
    }
}

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked {
        turnLeft()
        turnLeft()
    }
}

func getGem() {
    if isOnGem {
        collectGem()
        gemCounter += 1
        portalCheck()
    }
}

while gemCounter < 4 {
    nav()
    getGem()
}

//Corners of the World

greenPortal.isActive = false
orangePortal.isActive = false

var gemCount = 0
var switchCount = 0

func rightRuleNav() {
    if isBlockedRight && isBlocked {
        turnLeft()
    } else if isBlockedRight {
        moveForward()
    }  else {
        turnRight()
        moveForward()
    }
}

func gemOrSwitch() {
    if isOnGem {
        collectGem()
        gemCount += 1
    } else if isOnClosedSwitch {
        toggleSwitch()
        switchCount += 1
    }
}

func portalCheck() {
    if switchCount == 2 {
        greenPortal.isActive = true
    } else if switchCount == 3 {
        greenPortal.isActive = false
    }
}

turnLeft()
while switchCount != 6 || gemCount < 1 {
    rightRuleNav()
    gemOrSwitch()
    portalCheck()
}

//Random Gems Everywhere
//"gemCount < totalGems" is very difficult to visualize in my head. This had me very confused. It didn't help that, because they're both 0, then "0 < 0" which is... true? So someone online suggested adding the "or gemCount < 1" which gets the character moving.

let totalGems = randomNumberOfGems
var gemCount = 0

pinkPortal.isActive = true
bluePortal.isActive = true

func nav() {
    if !isBlocked {
        moveForward()
    } else if isBlocked && pinkPortal.isActive == true {
        pinkPortal.isActive = false
        bluePortal.isActive = false
        turnAround()
    } else if isBlocked && pinkPortal.isActive == false {
        pinkPortal.isActive = true
        bluePortal.isActive = true
        turnAround()
    }
}

func turnAround() {
    turnLeft()
    turnLeft()
}

func getGem() {
    if isOnGem {
        collectGem()
        gemCount += 1
    }
}

while gemCount < totalGems || gemCount < 1 {
    nav()
    getGem()
}