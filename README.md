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
First Person Camera Tutorial
-------------------------------
08/01/2025
Started my First Person Camera Tutorial that I was using in my prototype game.

09/01/2025
Finished write up for First Person Camera Tutorial

-------------------------------
First Person Movement Tutorial
-------------------------------

02/02/2025
I wanted my player to be able to jump and have a delay inbetween jumps so that it wasn't spammable. I had never programmed this before so I researched using Unity docs and videos to help me.
