# CS-Class
/**
 * Created by halen on 11/5/2015.
 */
public class Fraction {
    /**
     * The numerator of the fraction.
     */
    public int numerator;
    public int denominator;

    public Fraction(int num, int denom) {
        numerator = num;
        denominator = denom;
    }

    //time to simplify!~ define gcd method
    public static int gcd(int a, int b)
    {
        while(a!=0 && b!=0) // until either one of them is 0
        {
            int c = b;
            b = a%b;
            a = c;
        }
        return a+b; // either one is 0, so return the non-zero value
    }

    //access methods
    public int getNumerator() {
        return numerator;
    }

    public int getDenominator() {
        return denominator;
    }

    // add!
    public static Fraction add(Fraction frac1, Fraction frac2) {
        int numerator = (frac1.getNumerator() * frac2.getDenominator()) + (frac2.getNumerator() * frac1.getDenominator());
        int denominator = frac1.getDenominator() * frac2.getDenominator();

        return new Fraction(numerator / gcd(numerator, denominator), denominator / gcd(numerator, denominator));
    }

    //subtract!
    public static Fraction subtract(Fraction frac1, Fraction frac2) {
        int numerator = (frac1.getNumerator() * frac2.getDenominator()) - (frac2.getNumerator() * frac1.getDenominator());
        int denominator = frac1.getDenominator() * frac2.getDenominator();
        return new Fraction(numerator / gcd(numerator, denominator), denominator / gcd(numerator, denominator));
    }

    //multiply!!
    public static Fraction multiply(Fraction frac1, Fraction frac2) {
        int numerator = frac1.getNumerator() * frac2.getNumerator();
        int denominator = frac1.getDenominator() * frac2.getDenominator();
        return new Fraction(numerator / gcd(numerator, denominator), denominator / gcd(numerator, denominator));
    }

    //divide!!!
    public static Fraction divide(Fraction frac1, Fraction frac2) {
        int numerator = frac1.getNumerator() * frac2.getDenominator();
        int denominator = frac2.getNumerator() * frac1.getDenominator();
        return new Fraction(numerator / gcd(numerator, denominator), denominator / gcd(numerator, denominator));
    }
    public String toString()
    {
        String fraction1 = numerator + " / " + denominator;
        return fraction1;
    }
}


