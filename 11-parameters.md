Chapter 11 — Parameters

//I'm not sure why it took me to the end of this chapter to stop writing "character" and "expert" over and over; "blue" and "red" is so much simpler!

//Moving Further Forward

let expert = Expert()
func move(distance: Int) {
for i in 1 ... distance {
        expert.moveForward()
    }
}

move(distance: 6)
expert.turnRight()
move(distance: 2)
expert.turnRight()
move(distance: 5)
expert.turnLeft()
move(distance: 5)
expert.turnLeft()
expert.turnLockUp()
expert.turnLeft()
move(distance: 3)
expert.turnRight()
move(distance: 3)
expert.turnRight()
move(distance: 4)
expert.collectGem()

//Generalizing a Function

let expert = Expert()
let character = Character()
func turnLockUp(up: Bool, numberOfTimes: Int) {
for i in 1 ... numberOfTimes {
        if up == true {
            expert.turnLockUp()
        } else if up == false {
            expert.turnLockDown()
        }
    }
}

func turnAround() {
    expert.turnLeft()
    expert.turnLeft()
}

turnLock(up: true, numberOfTimes: 3)
turnAround()
turnLock(up: true, numberOfTimes: 3)
character.move(distance: 3)
character.collectGem()
character.turnRight()
character.turnRight()
character.moveForward()
character.turnLeft()
character.moveForward()
character.turnLeft()
turnLock(up: false, numberOfTimes: 3)
turnAround()
turnLock(up: false, numberOfTimes: 2)
character.moveForward()
character.collectGem()
character.turnRight()
character.turnRight()
character.moveForward()
turnLock(up: false, numberOfTimes: 1)
character.move(distance: 2)
character.collectGem()

//Crank Up and Down
//I went back and recycled the old right hand wall code from Chapter 7 to make the Character navigate and collect gems. The most time consuming part is testing, as I had the Expert working all four locks at the start of each run.

let expert = Expert()
let character = Character()
var gemCount = 0

func nav() {
    if character.isBlockedRight && character.isBlocked {
        character.turnLeft()
    } else if character.isBlockedRight {
        character.moveForward()
    }  else {
        character.turnRight()
        character.moveForward()
    }
}

func doLocksUp() {
    for i in 1 ... 4 {
        expert.turnLock(up: true, numberOfTimes: 4)
        expert.turnRight()
    }
}

func doLocksDown() {
    for i in 1 ... 4 {
        expert.turnLock(up: false, numberOfTimes: 3)
        expert.turnRight()
    }
}

doLocksUp()

while gemCount < 3 {
    nav()
    if character.isOnGem {
        character.collectGem()
        gemCount += 1
    }
}

character.turnRight()
character.moveForward()
character.turnLeft()

doLocksDown()

while gemCount < 7 {
    nav()
    if character.isOnGem {
        character.collectGem()
        gemCount += 1
    }
}

//Placing at a Specific Location
//How cool would it be to have the ability to teleport yourself all over the world? Probably this cool.

let expert = Expert()

world.place(expert, atColumn: 1, row: 6)
expert.collectGem()

world.place(expert, atColumn: 6, row: 1)
expert.collectGem()

world.place(expert, atColumn: 1, row: 1)
expert.collectGem()

//Rivers to Cross
//Look, if they're going to give me the cheat codes, I'm going to use the cheat codes. Locks? Pffft.

let character = Character()

world.place(character, facing: .north, atColumn: 5, row: 1)
character.collectGem()
character.moveForward()
character.collectGem()

world.place(character, facing: .north, atColumn: 5, row: 4)
character.collectGem()
character.moveForward()
character.collectGem()
character.turnLeft()
character.moveForward()
character.collectGem()

world.place(character, facing: .north, atColumn: 1, row: 5)
character.collectGem()
character.moveForward()
character.collectGem()
character.moveForward()
character.collectGem()
character.moveForward()
character.collectGem()

//Placing Two Characters
//So I didn't use the world.place "cheat" this time and tried to make a legitimately robust and efficient function for moving the Character, but I think the last few manually entered steps are a bit of a hack. It works, but I'm not proud! (I am proud of my function name, though!)

let character = Character()
let expert = Expert()

func doTheMario() {
    if character.isBlockedRight && character.isBlocked {
        character.turnRight()
        character.jump()
    } else if !character.isBlockedLeft && !character.isBlockedRight {
        character.turnLeft()
        character.move(distance: 2)
        character.collectGem()
        character.turnRight()
        character.turnRight()
    } else if character.isBlocked {
        character.jump()
    }
}

world.place(expert, facing: .north, atColumn: 3, row: 0)
expert.turnLockUp()
expert.toggleSwitch()

world.place(character, facing: .north, atColumn: 0, row: 0)
while character.isBlocked {
    if character.isOnGem {
        character.collectGem()
    }
    doTheMario()
}

//Two Experts

let expertAlpha = Expert()
let expertBeta = Expert()

world.place(expertAlpha, facing: north, atColumn: 0, row: 0)
world.place(expertBeta, facing: north, atColumn: 0, row: 4)

func alphaMove() {
    expertAlpha.turnRight()
    expertAlpha.move(distance: 3)
}

func betaMove() {
    expertBeta.turnRight()
    for i in 1 ... 7 {
        if expertBeta.isOnGem {
            expertBeta.collectGem()
        }
    expertBeta.moveForward()
    }
}

expertAlpha.collectGem()
alphaMove()
expertAlpha.turnLeft()
expertAlpha.turnLock(up: true, numberOfTimes: 2)
expertBeta.turnLockDown()
alphaMove()
expertAlpha.turnLock(up: false, numberOfTimes: 2)
betaMove()

//Twin Peaks
//I know this solution isn't perfect, but I like it. I didn't know I could put an if statment inside a for loop (like in the jumpX function). I was having problems figuring out how to get "Blue" to actually collect the gems. Originally the entire "if blue.isOnGem" statment was in the while loop above nav(), but this was causing Blue to plow right past the gems (unless it happened to stop on a corner with a gem). But because Playgrounds gives me immediate visual feedback (like writing HTML and refreshing the browser) I was able to quickly copy and paste the code into the for loop and see that, not only did it _not_ give me a red dot (indicating an error) but I was able to run the code and see Blue stop to collect each gem. I think, as a visual learner, this really helps me understand not just what the code is doing each step of the way, but how I can modify it to make it work better.

let red = Expert()
let blue = Character()
var gemCount = 0

func jumpX(distance: Int) {
    for i in 1 ... distance {
        blue.jump()
        if blue.isOnGem {
            blue.collectGem()
            gemCount += 1
        }
    }
    blue.turnRight()
}

func nav() {
    jumpX(distance: 6)
    jumpX(distance: 2)
}

world.place(red, facing: .north, atColumn: 0, row: 4)
red.turnLock(up: true, numberOfTimes: 2)
world.place(blue, facing: .south, atColumn: 4, row: 6)

while totalGems > gemCount || gemCount < 1 {
    nav()
}