# Usage of Trigonometry.

Trigonometric functions are basic functions that are very useful in dealing with coordinate axis maps as we do on codingame. It allows you to simplify the processes that are involved.

The most basic uses of trigonometry are seen in multiplayer games like Coders Strike Back. In such physics oriented games, a lot of vector algebra is used and proper use of trigonometry is a necessity.
For example, take this code that is used to calculate the resultant velocity after applying a thrust.
```
public void boost(int thrust)
    {


        float ra = this.angle * PI / 180.0f;


        this.velocity.x += (float)Math.Cos(ra) * thrust;
        this.velocity.y += (float)Math.Sin(ra) * thrust;
    }
```
