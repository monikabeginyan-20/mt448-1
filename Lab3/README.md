3. String, Formatting, Enum Switch,
    * ստեղծել Movie.cs կլասսը որը կպարունակի [ֆիլմի համարը, ֆիլմի անունը, տարեթիվը, ֆիլմի ժանրը, դիտումների քանակը, լայքերի քանակը]
    * ֆիլմի ժանրի համար ստեղծել enum 5 տարբերակ պարունակող, ըստ ձեր  հայեցողությամբ
    * Մուրտքագրումը կատարել Console-ից ReadLine() մեթոդով, ժանրը գրել որպես 1 ից 5 թիվ, որից հետո ինֆորմացիան տարանջատել (split) և տեղավորել կլասսի դաշտերում.
    * ստեղծել նաև մեթոդ որը կհաշվի ֆիլմի ռեյտինգը հետևյալ բանաձևով SQRT(Likes ^ 2 / Views) կլինի double տիպի;
    * Movie.cs կլասսի համար override անել ToString() մեթոդը որը ցույց կտա կլասսի պարունակությունը հետևյալ կերպ
        - ֆիլմի համարը, {4 տառաչափ, կցել աջ}
        - ֆիլմի անունը, {15 տառաչափ, կցել ձախ}
        - տարեթիվը,    {8 տառաչափ, կցել ձախ և փակագծերի մեջ օր․"(2011)"}
        - ֆիլմի ժանրը,  {12 տառաչափ, տեքստային, կցել ձախ}
        - ռեյտինգը {8 տառաչափ, ստրոակետրից հետո 1000-րդական ճշտությամբ, անպայման ցույց տա նաև եթե զրոներ են}
    * ցույց տալ կլասսի ֆունկիոնալությունը Main() մեթոդում, ծրագիրը սկզբում կընդհունի քանակը օրինակ 7 և հետո ցիկլով կնդունի 7 հատ ֆիլմի տվյալներ, այնուհետև ցիկլով ցույց կտա ֆորմատավորված տեսքով։  
    * որպեսզի ավելորդ չբարդացնեք բոլոր մեմբերները և մեթոդները ստեղծել public

    ```
    using System;

public enum MovieGenre
{
    Action = 1,
    Comedy = 2,
    Drama = 3,
    Horror = 4,
    SciFi = 5
}

public class Movie
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int Year { get; set; }
    public MovieGenre Genre { get; set; }
    public int Views { get; set; }
    public int Likes { get; set; }

    public Movie(int id, string title, int year, MovieGenre genre, int views, int likes)
    {
        Id = id;
        Title = title;
        Year = year;
        Genre = genre;
        Views = views;
        Likes = likes;
    }

    public double CalculateRating()
    {
        if (Views <= 0) return 0.0;
        return Math.Sqrt((double)(Likes * Likes) / Views);
    }

    public override string ToString()
    {
        double rating = CalculateRating();
        string yearFormatted = $"({Year})";
        string genreString = Genre.ToString(); // Թիվը վերածում ենք տեքստի (օրինակ՝ Action, Comedy...)
        
        return $"{Id,4} {Title,-15} {yearFormatted,-8} {genreString,-12} {rating,8:0.000}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Console.Write("Enter count: ");
        if (!int.TryParse(Console.ReadLine(), out int n))
        {
            return;
        }

        Movie[] movies = new Movie[n];

        Console.WriteLine("Enter data format: Id, Title, Year, Genre(1-5), Views, Likes");
        Console.WriteLine("Example: 1, Inception, 2010, 5, 1500, 1200\n");

        for (int i = 0; i < n; i++)
        {
            Console.Write($"Movie {i + 1}: ");
            string input = Console.ReadLine();
            
            if (string.IsNullOrWhiteSpace(input))
            {
                i--;
                continue;
            }

            string[] parts = input.Split(',');

            if (parts.Length < 6)
            {
                Console.WriteLine("Error: Please provide all 6 fields separated by commas!");
                i--;
                continue;
            }

            try
            {
                int id = int.Parse(parts[0].Trim());
                string title = parts[1].Trim();
                int year = int.Parse(parts[2].Trim());
                
                int genreVal = int.Parse(parts[3].Trim());
                if (genreVal < 1 || genreVal > 5)
                {
                    Console.WriteLine("Error: Genre must be a number between 1 and 5!");
                    i--;
                    continue;
                }
                MovieGenre genre = (MovieGenre)genreVal;

                int views = int.Parse(parts[4].Trim());
                int likes = int.Parse(parts[5].Trim());

                movies[i] = new Movie(id, title, year, genre, views, likes);
            }
            catch (Exception)
            {
                Console.WriteLine("Error parsing values. Try again.");
                i--;
            }
        }

        Console.WriteLine("\nResult:");
        foreach (var movie in movies)
        {
            Console.WriteLine(movie.ToString());
        }
    }
}՝՝՝
