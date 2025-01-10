# Portal Gun

This feature lets the player shoot a portal with their gun along with a portal placement method which is explained below. The gun is stuck to the player and its rotation follows the position of the mouse.

## Mechanism

### Portal Picking

There are 2 pairs/sets of portals which in total is 4 portals. The player can switch between using the 1st set or the 2nd set by pressing Shift. Pressing LMB will shoot the 1st portal of the set and RMB will shoot the 2nd portal of the set.
- _isSecondSet == false and Pressed LMB -> 1st Portal
- _isSecondSet == false and Pressed RMB -> 2nd Portal 
- _isSecondSet == true and Pressed LMB -> 3rd Portal
- _isSecondSet == true and Pressed RMB -> 4th Portal

### Portal Placement

When the projectile lands it checks for each main directions (up, right, down, left) and for each relative right and left how many solid cells are in the way with the width of 2.
- If there are cells in one way but not the other, then check the other way if the portal can fit when translated at most half of the portal's length
- If there are cells in both ways, then the portal can't be placed there.
- If there are no cells in both ways, then the portal can be immidiently placed there.
From those 4 directions, the one with the least translations is selected.

## Components
- GunMovement.cs: Behaviour of the gun movement, following the player's mouse position.
- GunShootingBehaviour.cs: Behaviour of the shooting mechanism of the gun, including projectile instantiation and cooldown.
- PortalInstanceManager.cs: Singleton to store portal instances.
- PortalProjectileBehaviour.cs: Behaviour of the portal projectile, from its initial speed to its lifetime duration. When the projectile collides with a solid object, it triggers itself and spawns a portal according to its transform. It is triggered either when it hits a solid object or when its lifetime duration is over.