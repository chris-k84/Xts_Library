# Collision Avoidance Overview

The Collision Avoidance concept is a fundemantal part of the XTS operation. Essentially an overriding mechanism that observes the commanded motions of the XTS movers and applies limits to movement to prevent collisions. This can include slowing even stopping movers who are about to collide. It takes precendence over the motion commands and so commanding a mover to move within a specified gap distance to another mover will result in the command waiting, until the path is clear.



