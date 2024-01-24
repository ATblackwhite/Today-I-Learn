Unity有特定的方法能让物体在碰撞时触发
[[OnTriggerEnter(触发器触发方法)]]
触发器和碰撞器非常相似，区别是碰撞器碰撞时会阻碍物体运动，但触发器不会。
方法为
```C#
void OnCollisionEnter(Collision collision)
{
    if(collision.collider.name == "Obstacle")
       Debug.Log("We hit something");
}
```
其中，collision为碰撞的信息，你可以在其属性中查找与之相碰撞的物体的信息