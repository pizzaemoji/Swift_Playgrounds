//Chapter 7 — Algorithms

//Had a lot of fun with these puzzles. It feels like, by this point, things are starting to click.

//The Right-Hand Rule

func navigateAroundWall() {
    if isBlockedRight {
        moveForward()
    }  else {
        turnRight()
        moveForward()
    }
}

func turnAround() {
    turnLeft()
    turnLeft()
}

while !isOnClosedSwitch {
    if isOnGem {
        collectGem()
        turnAround() 
    }
    navigateAroundWall()
}

toggleSwitch()

//Adjusting Your Algorithm

func navigateAroundWall() {
    if isBlockedRight && isBlocked {
        turnLeft()
    } else if isBlockedRight {
        moveForward()
    }  else {
        turnRight()
        moveForward()
    }
}
    
while !isOnClosedSwitch {
    navigateAroundWall()
    if isOnGem {
        collectGem()
        turnLeft()
        turnLeft()
    }
}

toggleSwitch()

//Conquering a Maze

func navigateAroundWall() {
    if isBlockedRight && isBlocked {
        turnLeft()
    }  else if isBlockedRight {
        moveForward()
    }  else {
        turnRight()
        moveForward()
    }
}
    
while !isOnGem {
    navigateAroundWall()
}

collectGem()

//Which Way to Turn?

func navMazeSwitch() {
    if isOnClosedSwitch && !isBlocked {
        toggleSwitch()
        turnRight()
    } else if isOnClosedSwitch {
        toggleSwitch()
        turnLeft()
    } else {
        moveForward()
    }
}

while !isOnGem {
    navMazeSwitch()
}

collectGem()

//Roll Right, Roll Left
//That's a lot of else if statements. There is probably a more efficient and easy solution to this, but it's late.

func navMaze() {
    if isOnGem && isBlocked {
        collectGem()
        turnRight()
        moveForward()
    } else if isOnGem {
        collectGem()
        moveForward()
    } else if isOnClosedSwitch && isBlocked {
        toggleSwitch()
        turnLeft()
        moveForward()
    } else if isOnClosedSwitch {
        toggleSwitch()
        moveForward()
    } else if isBlocked && isBlockedRight {
        turnLeft()
        moveForward()
    } else if isBlocked && isBlockedLeft {
        turnRight()
        moveForward()
    } else {
        moveForward()
    }
}

while !isOnOpenSwitch {
    navMaze()
}