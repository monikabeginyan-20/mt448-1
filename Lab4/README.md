4. using in, out, ref, params, and parameters by default values,
    * Ստեղծել static A(), B(), C() մեթոդները, համապատասխանաբար in, out, ref, մոդֆիկատորները փորձարկելու համար  
    * Ստեղծել նաև SumValues(parasm … ) մեթոդը որը կգումարի մուտքում եկած ամբողջ թվերը, թվերի քանակը ֆիքսված չէ
    * ցույց տալ թե ինչպես են աշխատում այս մեթոդները, Main() մեթոդում

```
class Program
{
    public static void A(in int x)
    {
        int result = x * 2;
        Console.WriteLine($"In method A: {result}");
    }

    public static void B(out int x)
    {
        x = 10;
        Console.WriteLine($"In method B: {x}");
    }

    public static void C(ref int x)
    {
        x += 5;
        Console.WriteLine($"In method C: {x}");
    }

    public static int SumValues(params int[] numbers)
    {
        int sum = 0;
        foreach (int num in numbers)
        {
            sum += num;
        }
        return sum;
    }

    public static void DefaultParamMethod(int x = 5, int y = 10)
    {
        Console.WriteLine($"Default params: x = {x}, y = {y}");
    }

    static void Main(string[] args)
    {
        int valA = 20;
        A(in valA);

        int valB;
        B(out valB);

        int valC = 15;
        C(ref valC);
        Console.WriteLine($"After ref: {valC}");

        int sum = SumValues(1, 2, 3, 4, 5);
        Console.WriteLine($"Sum: {sum}");

        DefaultParamMethod();
        DefaultParamMethod(50, 100);
    }
}```
