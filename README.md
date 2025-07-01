# Module-3-EBAC

Scene created for exercise of module-3-EBAC. A class called Maze (GroundObject) was added to the scene containing an int speed variable capable of being changed by pressing the A key. To play, use arrow keys to rotate the Maze (ground object) and A/S to change speed and guide the orb to the end.

Code

using UnityEngine;

public class GroundObjectController : MonoBehaviour

{

    #region Variables  
    public int speed = 15; // Speed of the ground object  
    #endregion  
    #region Methods  
    // Start is called once before the first execution of Update after the MonoBehaviour is created  
    void Start()
    {
        print ("Maze game started. Use arrow keys to rotate the Maze (ground object) and A/S to change speed and guide the orb to the end.");
    }
    // Update is called once per frame  
    void Update()
    {
        #region Speed Control Inputs
        // This section handles the speed control of the ground object based on key inputs 
        // Press A or S to change the rotation speed of the ground object
        if (Input.GetKeyDown(KeyCode.A))
        {
            speed += 1; // Increase the speed by 1 when A is pressed
            Debug.Log("Speed increased to: " + speed);
        }
        if (Input.GetKeyDown(KeyCode.S))
        {
            speed -= 1; // Decrease the speed by 1 when S is pressed
            Debug.Log("Speed decreased to: " + speed);
        }
        if (speed < 1) // Ensure speed does not go below zero
        {
            speed = 1;
            Debug.Log("Speed cannot be zero. Reset to 1.");
        }
        if (speed > 25) // Ensure speed does not exceed 25
        {
            speed = 25;
            Debug.Log("Speed cannot exceed 25. Reset to 25.");
        }
        #endregion
        #region Rotation Control Inputs
        // This section handles the rotation of the ground object based on arrow key inputs
        // Get the current rotation of the ground object based on the keys pressed. We will be altering this value and re-applying it  
        Vector3 newRotation = transform.localEulerAngles;
        if (Input.GetKey(KeyCode.RightArrow))
        newRotation.z -= Time.deltaTime * speed;
        if (Input.GetKey(KeyCode.LeftArrow))
        newRotation.z += Time.deltaTime * speed;
        if (Input.GetKey(KeyCode.UpArrow))
        newRotation.x -= Time.deltaTime * speed;
        if (Input.GetKey(KeyCode.DownArrow))
        newRotation.x += Time.deltaTime * speed;
        // Apply the updated rotation to the ground object  
        transform.localEulerAngles = newRotation;
    }   
        #endregion
    #endregion Methods  
}
