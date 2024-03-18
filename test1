using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> results = new List<string> { "3:1", "2:2", "0:1", "4:2", "3:a", "3- 12" };
        Dictionary<string, int> points = CalculatePoints(results);
        
        foreach(var team in points)
        {
            Console.WriteLine($"Команда {team.Key} набрала {team.Value} очков.");
        }
    }

    static Dictionary<string, int> CalculatePoints(List<string> results)
    {
        Dictionary<string, int> points = new Dictionary<string, int>();

        foreach (string result in results)
        {
            string[] parts = result.Split(':');
            
            if (parts.Length == 2 && int.TryParse(parts[0], out int homeScore) && int.TryParse(parts[1], out int awayScore))
            {
                if (homeScore > awayScore)
                {
                    string homeTeam = "Команда №1";
                    points[homeTeam] = points.GetValueOrDefault(homeTeam, 0) + 3;
                }
                else if (homeScore == awayScore)
                {
                    string homeTeam = "Команда №1";
                    string awayTeam = "Команда №2";
                    points[homeTeam] = points.GetValueOrDefault(homeTeam, 0) + 1;
                    points[awayTeam] = points.GetValueOrDefault(awayTeam, 0) + 1;
                }
                else
                {
                    string awayTeam = "Команда №2";
                    points[awayTeam] = points.GetValueOrDefault(awayTeam, 0) + 3;
                }
            }
            else
            {
                Console.WriteLine($"Ошибка в формате результата: {result}. Результат не будет учтен.");
            }
        }

        return points;
    }
}
