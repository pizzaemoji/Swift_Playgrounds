//Chapter 10 — Initialization

//So... "expert" is the constant, and "Expert()" is the type, or the value? Swift Playground's explanations sometimes are a little light on details. I get that they're trying to keep it approachable but I feel like I might be missing some key fundamentals as I move through these chapters. I'm still having fun, though!

//Initializing Your Expert

let expert = Expert()

expert.moveForward()
expert.moveForward()
expert.moveForward()
expert.turnLockUp()

for i in 1 ... 3 {
    turnAround()
    expert.moveForward()
    expert.moveForward()
    expert.moveForward()
    expert.turnRight()
    expert.moveForward()
    expert.moveForward()
    expert.moveForward()
    expert.collectGem()
}

func turnAround() {
    expert.turnLeft()
    expert.turnLeft()
}

//Train Your Expert

let expert = Expert()
var gemCount = 0

func navRight() {
    if !expert.isBlocked && !expert.isBlockedLeft {
        expert.turnRight()
        expert.moveForward()
    } else if expert.isBlocked {
        turnAround()
    } else {
        expert.moveForward()
    }
}

func turnAround() {
    expert.turnLeft()
    expert.turnLeft()
}

func getGem() {
    if expert.isOnGem && gemCount == 2{
        expert.collectGem()
        gemCount += 1
        expert.turnLockDown()
    } else if expert.isOnGem {
        expert.collectGem()
        gemCount += 1
    }
}

while gemCount < 6 {
    navRight()
    getGem()
}

//Using Instances of Different Types

let expert = Expert()
let character = Character()

expert.moveForward()
expert.turnLockUp()

character.moveForward()
character.collectGem()
character.moveForward()
character.turnRight()
character.moveForward()
character.moveForward()

expert.turnLockDown()
expert.turnLockDown()

character.moveForward()
character.collectGem()

//It Takes Two

let expert = Expert()
let character = Character()

func purpleSide() {
    expert.turnLeft()
    expert.moveForward()
    expertTwoSteps()
    expert.turnRight()
    expertTwoSteps()
    expert.turnLeft()
    expert.turnLockDown()
    expert.turnLockDown()
    expert.turnRight()
    expertTwoSteps()
    expert.turnRight()
    expertTwoSteps()
    expertTwoSteps()
}

func greenSide() {
    expertTwoSteps()
    expert.turnRight()
    expertTwoSteps()
    expert.turnLeft()
    expert.turnLockUp()
    expert.turnRight()
    expert.turnRight()
}

func expertTwoSteps() {
    for i in 1 ... 2 {
        expert.moveForward()
    }
}

func charTwoSteps() {
    for i in 1 ... 2 {
        character.moveForward()
    }
}

func gemAndSwitch() {
    charTwoSteps()
    character.collectGem()
    charTwoSteps()
    character.toggleSwitch()
}

purpleSide()
greenSide()
gemAndSwitch()