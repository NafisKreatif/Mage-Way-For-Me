# Obstacle Documentation

# Overview
The `IsDeath` class is a Unity MonoBehaviour script designed to detect collisions with a player character. The script is triggerred upon the character collide with certain obstacle object like spike and etc. When a collision is detected, it checks if the colliding object has a `PlayerMovement` component. If so, it triggers the `Die` method on the `PlayerMovement` script, simulating the player's death.

---
# Table of Content
1. [Class Description](#class-description)
2. [Methods](#methods)
   - [OnCollisionEnter2D](#oncollisionenter2d)
3. [Usage](#usage)
4. [Notes](#notes)

---

## Class Description

### `IsDeath`
This class extends Unity's `MonoBehaviour` and is primarily used to detect collisions in a 2D environment and handle player death logic.

---

## Methods

### `void OnCollisionEnter2D(Collision2D other)`
#### Description
This method is called automatically by Unity when another collider enters the collision boundary of the object to which this script is attached.

#### Parameters
- `other` (*Collision2D*): Provides details about the collision, including the collider of the other object.

#### Functionality
1. Checks if the colliding object has a `PlayerMovement` component.
2. If the `PlayerMovement` component exists, logs a "death" message to the Unity console.
3. Calls the `Die` method on the `PlayerMovement` instance.

#### Code

```csharp
private void OnCollisionEnter2D(Collision2D other)
{
    var player = other.collider.GetComponent<PlayerMovement>();
    if (player != null)
    {
        Debug.Log("death");
        player.Die();
    }
}