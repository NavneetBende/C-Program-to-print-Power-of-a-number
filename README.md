# C-Program-to-print-Power-of-a-number

Power of a number in C
In this program, we will calculate the power of a number in C programming.

Input:
Base : 3
Exponent : 4

Output:
81
Since, 34 = 81
power of number in c
Method discussed
Using inbuilt power function
Without inbuilt function
Handling Negative exponent when not using unbuilt function
Solving using recursion
Power of a Number in C
While loop in C
Method 1 (Using Power Function)
This method uses the inbuilt power function in the math.h library.

When it works/Doesn't
This method works always
1. Both Base & Exponent are integers (int).
2. Both Base & Exponent are decimals (double/float/long double).
3. When any/all of Base & Exponent are negative

Example:
25, (2.3)5.2 , (-3)-2 can be calculated
C Program:-
Run

// pow function is contained in math.h library

#include<stdio.h>
#include<math.h> 
int main() 
{
    double base = 2.3;
    double exp = 2.1;
    double result;
    
    // calculates the power
    result = pow(base, exp);
    
    // %lf used for double
    printf("%lf ^ %lf = %lf\n", base, exp, result);
    
    // following can be used for precision setting
    printf("%.1lf ^ %.1lf = %.2lf", base, exp, result);

    return 0;
}
Output:-
2.300000 ^ 2.100000 = 5.749479
2.3 ^ 2.1 = 5.75
While loop in C
Method 2 (Without inbuilt functions)
This method is suitable when we are not allowed to use inbuilt pow function.

When it works/doesn't
This method doesn't work when -
1. Exponent is decimal.
2. Exponent is negative.

Can be calculated:
25, (2.3)5 , (-3)2

Can not be calculated:
25.2, (3)-2
C Program:-
Run

#include<stdio.h>

int main() 
{
    double base = 2.32;
    // exp has to be positive and int value for this method
    int exp = 2;
    double result = 1.0;
    
    while (exp != 0) {
        result *= base;
        --exp;
    }
    
    printf("Answer = %lf", result);
    
    return 0;
}
Output:-
Answer = 5.382400
While loop in C
Method 3 (Without inbuilt functions)
This method solves the case of negative exponent with another while loop

How Negative Exponent issue is solved
base(-exponent) = 1 / (baseexponent)

For example, 2 -3 = 1 / (23)
When it works/Doesn't
This method doesn't work when -
1. Exponent is decimal.

Can be calculated:
25, (2.3)5 , (-3)2, (3)-2

Can not be calculated:
25.2
C Program:-
Run

#include<stdio.h>

int main() 
{
    double base = 2.32;
    // exp has to be int value. But, can be neg/pos both
    int exp = -2;
    double result = 1.0;
    
    // if exponent is positive
    while (exp > 0) {
        result *= base;
        --exp;
    }
    
    // if exponent is negative
    while (exp < 0) {
        result /= base;
        ++exp;
    }
    
    printf("Answer = %lf", result);
    
    return 0;
}
Output:-
Answer = 0.185791
While loop in C
Method 4 (Using Recursion)
This method solves the case of negative exponent with another while loop

When it works/Doesn't
This method doesn't work when -
1. Exponent is decimal.

Can be calculated:
25, (2.3)5 , (-3)2, (3)-2

Can not be calculated:
25.2
C Program:-
Run

#include<stdio.h>
double power(double base, int exp);
int main() 
{
    double base = 2.32;
    int exp = -2;
    double result = 1.0;
    
    result = power(base, exp);
    
    printf("%lf ^ %d = %lf", base, exp, result);
    
    return 0;
}

double power(double base, int exp) {
    if (exp > 0)
        return (power(base, exp - 1) * base);
    else if (exp < 0)
        return (power(base, exp + 1) / base);
    else
        return 1;
}
Output:-
Answer = 0.185791
