1. Class, Random, matrix, set get,  private public, constructor
    * ստեղծել Կլասս որը կպարունակի NxN չափերով մատրիցա
    * Կլասսում պահել private դաշտեր N, A և B, ամբողջ թվերի համար, և նրանց համար ապահովել {set get} մեթոդները կարճ գրելաձևով,
    * ստեղծել private FillMatrix անունեով մեթոդ, որը կլրացնի մատրիցայի արժեքները [A, B] միջակայքից պատական թվերով
    * ստեղծել public ShowMatrix մեթոդը, որը ցույց կարտածի մատրիցայի պարունակությունը
    * ստեղծել մեթոդ որը կվերադարձնի մատրիցայի կենտ թվերի քանակաը
    * պարամետրիզացված Կոնստրուկտորով տեղադրել N, A և B դաշտերի արժեքները որից հետո կանչել FillMatrix մեթոդը
    * ցույց տալ կլասսի ֆունկիոնալությունը Main() մեթոդում

```
using System;
using System.Linq;

class MatrixTask
{
    public int N { get; set; }
    public int A { get; set; }
    public int B { get; set; }

    private int[,] _matrix;

    public MatrixTask(int n, int a, int b)
    {
        N = n;
        A = a;
        B = b;
        _matrix = new int[N, N];
        FillMatrix();
    }

    private void FillMatrix()
    {
        Random rand = new Random();
        int min = Math.Min(A, B);
        int max = Math.Max(A, B);

        for (int i = 0; i < N; i++)
        {
            for (int j = 0; j < N; j++)
            {
                _matrix[i, j] = rand.Next(min, max + 1);
            }
        }
    }

    public void ShowMatrix()
    {
        Console.WriteLine($"Matrix {N}x{N} ([{A}, {B}]):");
        for (int i = 0; i < N; i++)
        {
            for (int j = 0; j < N; j++)
            {
                Console.Write($"{_matrix[i, j]}\t");
            }
            Console.WriteLine();
        }
    }

    public int GetOddCount() => _matrix.Cast<int>().Count(x => x % 2 != 0);
}

class Program
{
    static void Main(string[] args)
    {
        MatrixTask matrixObj = new MatrixTask(4, 1, 50);

        matrixObj.ShowMatrix();

        Console.WriteLine($"\nOdd count: {matrixObj.GetOddCount()}");
    }
}
```


