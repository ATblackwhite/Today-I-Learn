[[OnCollisionEnter(碰撞触发方法)]]
触发器和碰撞器非常相似，区别是碰撞器碰撞时会阻碍物体运动，但触发器不会。如果要让物体成为触发器，需要在Box Collider中将Is Trigger选项勾上
![[Pasted image 20231212170415.png]]
此时，该物体与其他物体碰撞时不会改变运动也不会触发OnCollisionEnter方法，而是触发OnTriggerEnter方法