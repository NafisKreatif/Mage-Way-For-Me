# Obstacle Mechanic

### Collision Detection

---

When any object collides with the GameObject that has this script attached, Unity's 2D physics system triggers the `OnCollisionEnter2D` method.

### Player Identification

---

The script checks whether the colliding object has a `PlayerMovement` component using the `GetComponent<PlayerMovement>()` method.

### Death Handling

---

If the colliding object has the `PlayerMovement` component:
- A "death" message is logged in the Unity console (`Debug.Log("death");`).
- The `Die` method from the `PlayerMovement` script is called to handle player death logic.