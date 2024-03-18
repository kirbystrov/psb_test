using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> results = GetResultsFromUser();
        Dictionary<string, int> points = CalculatePoints(results);
        
        foreach(var team in points)
        {
            Console.WriteLine($"Команда {team.Key} набрала {team.Value} очков.");
        }
    }

    static List<string> GetResultsFromUser()
    {
        List<string> results = new List<string>();
        Console.WriteLine("Введите результаты матчей через Enter (например, '3:1'). Для завершения введите '0':");

        while (true)
        {
            string input = Console.ReadLine();
            if (input == "0")
                break;
            
            results.Add(input);
        }

        return results;
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
                Console.WriteLine($"Ошибка в формате результата: {result}");
            }
        }

        return points;
    }
}
