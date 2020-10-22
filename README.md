# TCS-Ninja-coding-questions---1
Question:
Consider the below series:
1, 2, 1, 3, 2, 5, 3, 7, 5, 11, 8, 13, 13, 17, ...
This series is a mixture of 2 series - all the odd terms in this series form a Fibonacci series and all the even terms are the prime numbers in ascending order.
Write a program to find the Nth term in this series.

Program in JAVA :

public class SeriesFinder {
	public static boolean isSquare(int n) {
		if(Math.sqrt(n)*Math.sqrt(n) == n)
			return true;
		else
			return false;
	}
	
	public static boolean isfibo(int n) {
		if(isSquare(5*n*n+4)||isSquare(5*n*n-4))
			return true;
		else
			return false;
	}
	public static boolean isPrime(int n) {
		int cnt=0;
		for(int i=1;i<=n;i++) {
			if(n%i==0) {
				cnt++;
			}
		}
		if(cnt == 2) {
			return true;
		}
		else {
			return false;
		}
	}
	public static int NumberFinder(int number) {
		//even ->prime number
		int start=1;
		if(number%2==0) {
			int n = number/2;
			int cnt=0;
			do {
				if(isPrime(start)) {
					cnt++;
					start = start+1;
				}
				else {
					start = start+1;
				}
			}while(cnt!=n);
			return start-1;
		}
		// odd -> fibonacci number
		else {
			int cnt=0;
			int n = number/2;
			do {
				if(isfibo(start)) {
					cnt++;
					start+=1;
				}
				else {
					start+=1;
				}
			}while(cnt!=n);
			return start-1;
		}
		
	}
	public static void main(String[] args) {
		System.out.println(NumberFinder(5));
	}
}
