//Chapter 12 — World Building

//I find that as the playgrounds and code get more complex, the less stable Swift Playgrounds becomes.

//Uniting Worlds

let block33 = Block()
world.place(block33, atColumn: 3, row: 3)

func nav() {
    if isBlocked && isBlockedRight {
        turnLeft()
        moveForward()
    } else if isBlockedRight {
        moveForward()
    }  else {
        turnRight()
        moveForward()
    }
}

while !isOnClosedSwitch {
    nav()
}
toggleSwitch()

//Connect and Solve
//I think this is the first time I've written a while loop followed by an if statement. I'm not sure what to think of this solution. I tried to write it so the length of the paths and the locations of gems wouldn't affect the movements, so that feels right. But I also feel like writing it without the loops and ifs could have made the code much cleaner.

let block22 = Block()
let block42 = Block()
let block62 = Block()
var gemCount = 0

world.place(block22, atColumn: 2, row: 2)
world.place(block42, atColumn: 4, row: 2)
world.place(block62, atColumn: 6, row: 2)

func moveForwardUntilSwitch() {
    while !isOnClosedSwitch {
        moveForward()
    };
    if isOnClosedSwitch {
        toggleSwitch()
        turnRight()
    }
}

func moveForwardAndGetGem() {
    while !isOnGem {
        if !isBlocked {
            moveForward()
        } else if isBlocked {
            jump()
        }
    };
    if isOnGem {
        turnLeft()
        turnLeft()
        collectGem()
        gemCount += 1
    }
}

func returnToSwitch() {
    while !isOnOpenSwitch {
        if !isBlocked {
            moveForward()
        } else if isBlocked {
            jump()
        }
    };
    if isOnOpenSwitch {
        turnRight()
    }
}

while gemCount < 3 {
    moveForwardUntilSwitch()
    moveForwardAndGetGem()
    returnToSwitch()
}

//Making Your Own Portals

let greenPortal = Portal(color: #colorLiteral(red: 0.4028071761, green: 0.7315050364, blue: 0.2071235478, alpha: 1))

func nav() {
    for i in 1 ... 8 {
        if isBlockedLeft {
            moveForward()
        } else if !isBlockedLeft {
            turnLeft()
            moveForward()
            collectGem()
            turnRight()
            turnRight()
        }
    }
}

nav()
world.place(greenPortal, atStartColumn: 1, startRow: 5, atEndColumn: 5, endRow: 1)
moveForward()
greenPortal.isActive = false
nav()

//Reach for the Stairs

var switchCount = 0

world.place(Stair(), facing: .south, atColumn: 3, row: 1)
world.place(Stair(), facing: .south, atColumn: 3, row: 3)
world.place(Stair(), facing: .east, atColumn: 5, row: 4)
world.place(Stair(), facing: .east, atColumn: 5, row: 6)
world.place(Stair(), facing: .north, atColumn: 4, row: 7)
world.place(Stair(), facing: .north, atColumn: 2, row: 7)
world.place(Stair(), facing: .west, atColumn: 1, row: 6)
world.place(Stair(), facing: .west, atColumn: 1, row: 4)

move(distance: 4)
turnRight()
move(distance: 2)

while switchCount < 9 {
    if !isBlockedRight {
        turnRight()
        moveForward()
    } else if isBlocked {
        turnLeft()
    } else if isBlockedRight {
        moveForward()
    }
    if isOnClosedSwitch {
        toggleSwitch()
        switchCount += 1
    }
}

//Floating Islands

let blue = Character()
let blackPortal = Portal(color: #colorLiteral(red: 0.0, green: 0.0, blue: 0.0, alpha: 1.0))
let whitePortal = Portal(color: #colorLiteral(red: 0.9999960065, green: 1.0, blue: 1.0, alpha: 1.0))
world.place(Block(), atColumn: 4, row: 4)
world.place(Block(), atColumn: 4, row: 4)
world.place(blue, facing: .south, atColumn: 4, row: 4)
world.place(blackPortal, atStartColumn: 5, startRow: 3, atEndColumn: 2, endRow: 3)
world.place(whitePortal, atStartColumn: 1, startRow: 2, atEndColumn: 3, endRow: 6)

func nav() {
    blue.turnLeft()
    blue.jump()
    blue.toggleSwitch()
    blue.jump()
    blue.collectGem()
    blue.turnRight()
    blue.jump()
    blue.toggleSwitch()
    blue.turnRight()
    blue.jump()
}

for i in 1 ... 3 {
    nav()
}

//Build a Loop
//Yes, I do recall how to disable a portal... but is that cheating?

let blue = Character()
var gemCount = 0

world.place(Block(), atColumn: 1, row: 3)
world.place(Block(), atColumn: 3, row: 3)
world.place(Block(), atColumn: 6, row: 3)
world.place(Block(), atColumn: 6, row: 0)
world.place(Block(), atColumn: 1, row: 0)
world.place(Block(), atColumn: 0, row: 2)
world.place(blue, facing: .south, atColumn: 7, row: 3)

bluePortal.isActive = false
yellowPortal.isActive = false
greenPortal.isActive = false

while totalGems > gemCount {
    if blue.isBlocked {
        blue.turnRight()
    } else {
        blue.moveForward()
    }
    if blue.isOnGem {
        blue.collectGem()
        gemCount += 1
    }
}

//A Puzzle of Your Own
