# Interactable Toggle

Featuring objects that can be interacted by player to toggle the activate state of an object.

## Mechanism

### Toggling Object

The interactable can toggle other object's active state when the player is on and not on the interactable.

### Door Object

This is one of the objects that can be toggled active and not. When active (toggled with interactive object), the door will open. Else, it will close.

## Components

- InteractableToggle.cs: storing the Toggle() function. Called in the Trigger_interactable.cs
- Trigger_interactable.cs: checking wether the player is on the interactable object or not. Calling Toggle() function when the player is either entering or exiting the interactable object collision.
- Door.cs: storing the behaviour of the door object.
