# Ex.No: 7  Implementation of Simple Pathfinding with Obstacles
### DATE: 03-11-2026                                                                   
### REGISTER NUMBER : 212225040177
### AIM: 
To write a program to pathfinding using AI navigation 
### Algorithm:
```
1. Create a New Unity Project by Open the  Unity Hub and create a new 3D Project,Name the project (e.g., Pathfinding).
2. Set Up the Scene by Create the Ground (Plane or Terrain)
  Go to: GameObject → 3D Object → Plane and Rename: "Ground"  Scale it: (10, 1, 10) (or adjust as needed)
3. Add Obstacles (Cubes or Walls)
  Go to: GameObject → 3D Object → Cube  Scale it: (3, 3, 1) (for a wall-like structure)
  Position it: Place it anywhere to block AI movement Rename it: "Obstacle"  Duplicate: Ctrl + D to create multiple obstacles ,tag the obstacke with same name.
4.Bake the NavMesh
Go to: Window → AI → Navigation , Select Ground: Click on your Ground object ,
In Navigation Window: Check ✅ "Navigation Static"  or Add component Navigation surface and Bake
5.Create the AI Character and Attach navMesh Agent
Go to: GameObject → 3D Object → Capsule ,  Rename: "AICharacter" , Scale: (1, 2, 1)
Go to: Inspector → Add Component → NavMeshAgent Adjust Settings: Speed: 3.5 Stopping Distance: 1  Obstacle Avoidance: High
6.Create the Script "AIPathFinder" (Go to: Assets → Right Click → Create → C# Script and  Rename it: "AIPathfinder"
7.Attach the Script"AIPathFinder" code by Drag & Drop the AIPathfinder.cs onto the AICharacter 
8.Assign the Target:Create a Target: GameObject → 3D Object → Sphere, Rename it: "Target",
 In AICharacter Inspector → AIPathfinder → Drag the Target Sphere into the "target" field.
9.Add NavMeshObstacle
Select an Obstacle (Cube)
Go to: Inspector → Add Component → NavMeshObstacle and Check: ✅ "Carve"
10.Move the Obstacle with Code ( attach it with Obstacle) 
11. Run the program
```  
### Program:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;
using static UnityEngine.GraphicsBuffer;

public class AIPathfinder : MonoBehaviour
{
    // Start is called before the first frame update
    public Transform target; // Assign the target in the Inspector
    private NavMeshAgent agent;
    void Start()
    {
        agent = GetComponent<NavMeshAgent>(); // Get the NavMeshAgent
    }

    // Update is called once per frame
    void Update()
    {
        agent.SetDestination(target.position);
    }
}
#Moving Obstacle
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Moving : MonoBehaviour
{
    // Start is called before the first frame update
    public float moveDistance = 3f;
    public float moveSpeed = 2f;
    private Vector3 startPos;
void Start()
    {
    startPos = transform.position;
    }

    // Update is called once per frame
    void Update()
    {
       float movement=Random.Range(-moveDistance / 14, moveDistance / 14);
        transform.position = startPos + new Vector3(movement, 0, 0);
    }
}
```
For smooth movement(optional)  -> use  
float movement = Mathf.PingPong(Time.time * moveSpeed, moveDistance) - moveDistance / 2;
transform.position = startPos + new Vector3(movement, 0, 0);
### Output:

<img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/75e69831-2474-48f1-b78a-0aec8a2e023c" />
<img width="1917" height="987" alt="image" src="https://github.com/user-attachments/assets/08a97438-71ed-4a26-8b96-d69f255d1488" />









### Result:
Thus the simple path finding  behavior was implemented using AI navigation successfully.
