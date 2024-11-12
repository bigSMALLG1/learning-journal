Tutorials
-------------------------------
Random Enemy Movement Tutorial
-------------------------------
12/11/2024

I decided to do a tutorial of a script I used last year for randomised enemy movement. I did this as it is simple to program and is easy to explain as it doesn't use complicated syntax and can be configured to the individuals needs.


(This tutorial demonstrates how you program enemies to move in random directions, changing the angle of their directions randomly within a certain timeframe that can be set by the programmer.)


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
