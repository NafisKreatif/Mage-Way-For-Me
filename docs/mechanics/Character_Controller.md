# Character Controller Documentation

## Overview
This documentation covers a 2D character controller implementation in Unity, there is four main components:
- Character Controller (CharacterController2D.cs)
- Player Movement (PlayerMovement.cs)
- Player Rotation Controller (PlayerRotationController.cs)
- Physics Material (friction.physicsMaterial2D)

## CharacterController2D Class
### Description
A base controller class that handles fundamental 2D character mechanics including movement, jumping, and ground detection.

### Properties
- `_jumpForce` (float): Force applied when the player jumps (default: 400f)
- `_movementSmoothing` (float): Smoothing factor for movement (range: 0-0.3f)
- `_airControl` (bool): Determines if the player can control movement while in air
- `_whatIsGround` (LayerMask): Defines what layers are considered ground
- `_groundCheck` (Collider2D): Reference to the ground detection collider

### Key Methods
#### `Move(float move)`
Controls horizontal movement of the character.
- **Parameters**: 
  - `move`: Horizontal movement value (-1 to 1)
- **Behavior**:
  - Applies movement only when grounded or air control is enabled
  - Automatically flips character sprite based on movement direction
  - Uses smooth damping for fluid movement

#### `Jump()`
Handles character jumping mechanics.
- **Returns**: bool - Whether the jump was successful
- **Behavior**:
  - Only allows jumping when grounded
  - Resets vertical velocity if falling
  - Applies jump force upward

## PlayerMovement Class
### Description
Handles player input and high-level movement control, working in conjunction with CharacterController2D.

### Properties
- `runSpeed` (float): Base movement speed (default: 40f)
- `_jumpBufferTime` (float): Time window for buffering jump inputs (default: 0.2f)
- `restartTime` (float): Delay before scene restart after death (default: 1.5f)

### Key Methods
#### `Die()`
Handles player death sequence.
- **Behavior**:
  - Disables player control
  - Applies death force and rotation
  - Triggers scene restart after delay

## PlayerRotationController Class
### Description
Manages character rotation corrections to maintain proper orientation.

### Properties
- `rotateDuration` (float): Time taken to complete rotation (default: 0.2f)
- `rotationDelay` (float): Delay before starting rotation (default: 0.2f)

### Key Methods
#### `RotateOverTime(Quaternion originalRotation, Quaternion finalRotation, float duration, float rotateAfter)`
Coroutine that handles smooth rotation transitions.
- **Parameters**:
  - `originalRotation`: Starting rotation
  - `finalRotation`: Target rotation
  - `duration`: Time to complete rotation
  - `rotateAfter`: Delay before starting rotation
- **Behavior**:
  - Uses Slerp for smooth rotation
  - Implements delay before rotation starts
  - Prevents multiple simultaneous rotations

## Physics Material (friction.physicsMaterial2D)
### Description
Physics material configuration for character movement.

### Properties
- `friction`: 0 (No friction)
- `bounciness`: 0 (No bounce)
- `FrictionCombine`: 1 (Average)
- `BounceCombine`: 4 (Maximum)

## Integration Guide
1. Attach `CharacterController2D` to the player GameObject
2. Add `PlayerMovement` script and reference the CharacterController2D
3. Attach `PlayerRotationController` for rotation handling
4. Apply the friction physics material to the player's collider
5. Set up ground detection collider and layer masks

## Input Requirements
- Horizontal movement: "Horizontal" axis
- Jump: "Jump" button
- Both configured in Unity's Input Manager

## Performance Considerations
- Ground detection uses OverlapCircleAll, consider optimization for large scenes
- Smooth damping on movement may need adjustment based on frame rate
- Jump buffer system helps with input responsiveness

## Notes
- Character can be configured for both air control and ground-only control
- Death sequence includes visual feedback with rotation and force
- Automatic scene reloading implemented after death
- Ground detection uses circular overlap for better precision