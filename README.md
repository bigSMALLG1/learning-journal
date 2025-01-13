Tutorials
-------------------------------
Enemy Following Player Tutorial
-------------------------------
29/10/2024

This tutorial is for a script that causes an object to follow another object which could be used for enemies tracking and folowing the player.

1/11/2024

I used the unity project for my prototype game to showcase this tutorial as the same script is used in my prototype.
I used unity docs and videos to help me learn how to program this as I had not attempted this in the 3D environment before. I found that you can program this using a single line of code, I just had to add a rigidbody component to the enemy for gravitational forces
to apply to it, so that the enemy wouldn't float in to the sky if my player jumped.

29/12/2024

Finished write up for Enemy Following Player tutorial, adjusted speed and added neccessary components.

-------------------------------
Random Enemy Movement Tutorial
-------------------------------
12/11/2024

I decided to do a tutorial of a script for randomised enemy movement. I did this as it is simple to program and is easy to explain as it doesn't use complicated syntax and can be configured to the individuals needs.
I had experience with making a similar script to this in the past, which is another reason as to why I chose it for my first tutorial.
I created a new unity project and created a 2D circle sprite and attached the script to it, I reduced the enemySpeed variable to 2f and also reduced the size of the sprite so that the sprite won't go off the screen as quickly in play mode.
Next I will start a written tutorial.
I may change this so that it is applicable to the 3D environment in my prototype game.

(This tutorial demonstrates how you program enemies to move in random directions, changing the angle of their directions randomly within a certain timeframe that can be set by the programmer).


The script:

using System.Collections;
using System.Collections.Generic;
using UnityEditor;
using UnityEngine;

public class enemyBehaviour : MonoBehaviour
{
    private float enemySpeed = 5f;
    private float minTime = 1f;
    private float maxTime = 3f;

    private Vector3 direction;
    private float timer;
   
    private void Start()
    {
        direction = Random.insideUnitSphere;
        timer = Random.Range(minTime, maxTime);
    }
    private void Update()
    {
        transform.Translate(direction * enemySpeed * Time.deltaTime);
        timer -= Time.deltaTime;

        if(timer <= 0f)
        {
            direction = Random.insideUnitSphere;
            timer = Random.Range(minTime, maxTime);
        }
    }
}

Originally I had not had the timer change its time randomly so the game objects would all change direction at the same time. I rectified this by having the timer set to a random value between 1 and 3 seconds every time the timer hit 0 which the <= allowed me to.

14/11/2024
I was having compiler errors when I tried testing the script and I could not find the issue. I then found that I had Random.insideUnitSphere was incorrectly spelt at the time.

25/11/2024 
Finished write up for the RandomEnemyMovement tutorial

-------------------------------
First Person Movement Tutorial
-------------------------------
01/01/2025

Started my First Person Camera Tutorial that I was using in my prototype game. 

Assigned script to the camera parent object as the script being used on the actual camera was buggy due to the rigidbody.

01/01/2025

Finished write up for First Person Camera Tutorial

-------------------------------
Jump Mechanic Tutorial
-------------------------------

01/01/2025

I planned to add this in to my prototype game which had my first person movement script, however my player was speeding off and had no ground drag so I added a ground check to my prototype game and added some ground drag when the player was grounded. I used a raycast for the ground check so that the player would jump only when it's bool variable (readyToJump) was true and that the bool variable (grounded) was true. I also added a speed limiter.

02/01/2025
I wanted my player to be able to jump and have a delay inbetween jumps so that it wasn't spammable. I had never programmed this before so I researched using Unity docs and videos to help me.


------------------------------
Prototype Game 
------------------------------

12/12/2024

I started my prototype game before I finished my tutorials as I wanted to use the scripts from the tutorials in my game, so I developed the scripts in the prototype and then made the tutorials from them excluding one.
To start off with I wanted to use first person movement which I had not used before. I had mostly only programmed in a 2D environment apart from when learning unity. It was not as simple as attaching the camera to the player, I had to account for moving the camera in accordance with moving the orientation of the player, as well as where the camera was positioned on to the player. I solved this by creating game objects for the camera, camera holder, camera position and orientation of the player and setting the camera position to the positition of the orientation of the player. 

15/12/2024

I added enemy gameobjects that track and follow the player. I used OnCollisionEnter on my player so that the enemies are destroyed on collision with the player. I would plan to turn this in to an explosion dealing damage to the player.

19/12/2024

In my game I wanted there to be a jump mechanic as a way of jumping over the small ankle biting enemies that chase you. In doing this I had issues with my player jumping very high in to the sky in the direction of where my mouse was pointed. To solve this I added an air multiplier to the movement speed when the player was not grounded, slowing down the jump. I also added a jump cooldown so that this could not be spammed, the cooldown would reset when the player was ready to jump and in contact with the ground which I also used a raycast to detect.

9/12/2024

I added a speedboost game object that doubles the players speed for 2 seconds. The speedboost is destroyed upon collision from the player. The speedboosts are triggers and I had issues with them disappearing when starting the game, I found out that I had rigidbodies on them and because they were triggers they were phasing through the ground terrain so I removed the rigidbodies.



