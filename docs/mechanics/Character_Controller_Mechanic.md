# Character Controller Mechanic

### Movement System

- Horizontal movement using Unity's input system
- Smooth damping for fluid motion
- Character flips based on movement direction
- Movement speed of 40 units/second

### Jump Mechanics

- Ground-check based jumping
- Jump buffer system (0.2s window)
- Jump force of 400 units
- Vertical velocity reset when falling

### Air Control

- Optional control while in air
- Same movement mechanics as ground movement
- Can be disabled for more challenging gameplay

### Rotation Control

- Automatic rotation correction
- 0.2s rotation duration
- 0.2s rotation delay

### Death System

- Disables player control
- pplies force and rotation based on last movement direction
- 1.5s delay before scene restart
- Automatic scene reload

### Physics Properties

- Zero friction for smooth movement
- No bounciness
- Custom collision detection
- Ground check using circular overlap

## The system functions as a cohesive unit where:

- Input is constantly monitored for movement and jumps
- Ground state is checked every physics update
- Movement and actions are processed based on ground state
- Rotation is corrected when needed
- Death triggers a sequence of events leading to restart