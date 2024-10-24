#include <bits/stdc++.h>
using namespace std;
const int MAX = 1000;
 
// Create an array for memorization
int f[MAX] = { 0 };
 
// Function to return the n'th Fibonacci
// number using table f[].
int fib(int n)
{
    // Base cases
    if (n == 0)
        return 0;
    if (n == 1 || n == 2)
        return (f[n] = 1);
 
    // If fib(n) is already computed
    if (f[n])
        return f[n];
 
    int k = (n & 1) ? (n + 1) / 2 : n / 2;
 
    // Applying recursive formula
    // Note value n&1 is 1
    // if n is odd, else 0.
    f[n] = (n & 1) ? (fib(k) * fib(k) + fib(k - 1) * fib(k - 1))
                   : (2 * fib(k - 1) + fib(k)) * fib(k);
 
    return f[n];
}
 
// Function to return gcd of a and b
int gcd(int a, int b)
{
    if (a == 0)
        return b;
 
    return gcd(b % a, a);
}
 
// Function to return the LCM of
// Fib(a) and Fib(a)
int findLCMFibonacci(int a, int b)
{
    return (fib(a) * fib(b)) / fib(gcd(a, b));
}
 
// Driver code
int main()
{
    int a = 3, b = 12;
 
    cout << findLCMFibonacci(a, b);
 
    return 0;
}
