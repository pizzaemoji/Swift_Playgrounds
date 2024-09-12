//Chapter 6 — While Loops

//And then they hit me with nesting while loops...

//Running Code While...

while isOnClosedSwitch {
	toggleSwitch()
    moveForward()
}

//Creating Smarter While Loops

while !isBlocked {
    if isOnClosedSwitch {
        toggleSwitch()
    } else {
        moveForward()
    }
}

//Choosing the Correct Tool

func turnAndCollectGem() {
    moveForward()
    turnLeft()
    moveForward()
    collectGem()
    turnRight()
}

while !isBlocked {
    turnAndCollectGem()
}

//Four by Four
//This was a tough one for me. I originally made it with the for loop, despite this being in the while loop chapter. So I came back and tried again, but I still think I prefer the for loop, although I understand the usefulness of the while loop. They're both listed here, fist the for loop:

for i in 1 ... 4 {
    moveForward()
    moveForward()
    moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    }
    turnRight()
}

//And the while loop:

while !isBlocked {
    moveForward()
    if isOnOpenSwitch {
        turnRight()
    }
    if isOnClosedSwitch {
        turnRight()
        toggleSwitch()
    }
}

//Turned Around
//I think the Playgrounds instructions for this puzzle make it sound more complicated than it needs to be. Originally I was trying to find a way to make the character move without each moveForward, turnLeft command. Then I had the whole series of commands as a function, and stuck my collectTwo func into a for loop. Then I realized the loop isn't needed if I just add another moveForward to the end of the while loop so the character is always on a gem (until there are no more gems). 11 lines? Seems pretty "efficient" to me.

moveForward()
while isOnGem {
    turnLeft()
    collectGem()
    moveForward()
    collectGem()
    turnLeft()
    moveForward()
    turnRight()
    moveForward()
}

//Land of Bounty
//I'm not a fan of this solution. While it gets the job done, it's just a little too verbose and rigid for my tastes. Maybe someday when I'm more confident with while loops I can give this another try.

func action() {
    while isOnClosedSwitch || isOnOpenSwitch {
        if isOnClosedSwitch {
            toggleSwitch()
        } else {
            moveForward()
        }
    }
    while isOnGem {
        collectGem()
        moveForward()
    }
}

func move() {
    if isBlocked && isBlockedLeft {
        turnRight()
        moveForward()
        turnRight()
        moveForward()
    }
    if isBlocked {
        turnLeft()
        moveForward()
        turnLeft()
        moveForward()
    }
        
}

moveForward()
action()
move()
action()
move()
action()

//Nesting Loops
//This simple puzzle was painful. I'm still not confident with these nested while loops.

while !isBlocked {
	while !isOnGem {
		moveForward()
	}
	collectGem()
	turnLeft()
}

//Random Rectangles

while !isBlocked {
    while !isOnClosedSwitch && !isBlocked {
        moveForward()
    }
    turnRight()
    toggleSwitch()
}

//You're Always Right

func forwardAndRight() {
    while !isBlocked {
        moveForward()
    if isOnClosedSwitch {
        toggleSwitch()
    }
    }
    turnRight()
}

while !isOnGem {
    forwardAndRight()
}
collectGem()
