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

Computing the series to 4 terms gives a very accurate result, and this is how the standard libraries perform any non-polynomial functions, this includes logarithmic, trigonometric and inverse trigonometric functions.
While this is useful, it is unfortunately very slow as there are several slow division operations involved.

# How to optimize them

The basis for optimization in this case is precomputation. Applying this to trigonometric functions, we can code our own functions after precomputing as the reciprocals of all involved factorials.
An example of this is:
```
public class TrigConstants
{
    public static double Fact_2 = 1.0 / Math.Factorial(2);
    public static double Fact_3 = 1.0 / Math.Factorial(3);
    public static double Fact_4 = 1.0 / Math.Factorial(4);
    public static double Fact_5 = 1.0 / Math.Factorial(5);
    public static double Fact_6 = 1.0 / Math.Factorial(6);
    public static double Fact_7 = 1.o / Math.Factorial(7);
}
```
We precompute the reciprocals as the division operator is a lot slower than the multiplication operator

After which we can make our own Trigonometric functions like this. 
```
public double sin(double angle)
{
    return 1 - Math.Pow(angle, 2) * TrigConstants.Fact_2 + Math.Pow(angle, 4) * TrigConstants.Fact_4 - Math.Pow(angle, 6) * TrigConstants.Fact_6;
}
```
This will speed up the functions considerably.
Additional optimizations can be made when the angle is between 0 and 1.
At this point, we can assume that x^6 / 6! is zero and exclude this term. 

Optimizing trig functions is very useful as performance is of utmost importance in search based bots.








