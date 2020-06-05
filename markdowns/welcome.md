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
In this playground, I will not focus on trigonometry, but rather how to make our computers run these functions faster. This is essential in optimizing the code for search based bots.

# How are the functions calculated

Trigonometric functions are not polynomials, they are on a branch of their own. So computing a function is not as easy as some multiplication and addition. In order to compute them, we make use of the Taylor Series.

The Taylor series is an infinute sum of the nth order derivatives of a function such that it converges to the function's actual value at that point.
The Taylor Series expansions for the most basic functions --> Sine and Cosine are:

```
Sin(x) = x - x^3 / 3! + x^5 / 5! - x^7/7! To infinity...

Cos(x) = 1 - x^2 / 2! + x^4 / 4! - x^6 / 6! To infinity...
```

In gen








