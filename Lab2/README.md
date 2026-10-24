2. Method overloading, default parameters,
    * Ստեղծել static ToMultiplicate մեթոդը, 3 օրինակով, որը կնդունի x, N փոփոխականները
    * N-ը կունենեա ըսկ լռելյայն (default) արժեք 2, կլինի int տիպի
    * իսկ x-ը կլինի երեք տարբերակով int, double և string
    * ֆունկցիան պիտի վերադարձնի N հատ x-երի գումարը, հատուկ սենց գրեցի որ string-ի դեպքն էլ հասկանալի լինի
    * թեստավորել overloading-ի աշխատանքը Main() մեթոդում

    ```
    using System;
using System.Text;

class Program
{
    public static int ToMultiplicate(int x, int N = 2)
    {
        return x * N;
    }

    public static double ToMultiplicate(double x, int N = 2)
    {
        return x * N;
    }

    public static string ToMultiplicate(string x, int N = 2)
    {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < N; i++)
        {
            sb.Append(x);
        }
        return sb.ToString();
    }

    static void Main(string[] args)
    {
        int resultInt1 = ToMultiplicate(5, 3);
        int resultInt2 = ToMultiplicate(4);

        double resultDouble1 = ToMultiplicate(2.5, 4);
        double resultDouble2 = ToMultiplicate(3.14);

        string resultString1 = ToMultiplicate("Monica ", 3);
        string resultString2 = ToMultiplicate("Beginyan");

        Console.WriteLine($"Int (5, 3) -> {resultInt1}");
        Console.WriteLine($"Int (4, default) -> {resultInt2}");
        Console.WriteLine($"Double (2.5, 4) -> {resultDouble1}");
        Console.WriteLine($"Double (3.14, default) -> {resultDouble2}");
        Console.WriteLine($"String (\"Monica \", 3) -> {resultString1}");
        Console.WriteLine($"String (\"Beginyan\", default) -> {resultString2}");
    }
}    
