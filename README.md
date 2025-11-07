using System;
using System.Linq; 

public class ArrayOperations
{
    public static int[] SortAscending(int[] arr)
    {
        if (arr == null)
        {
            return null; 
        }
        Array.Sort(arr); 
        return arr;
    }

   
    public static int[] SortDescending(int[] arr)
    {
        if (arr == null)
        {
            return null;
        }
        Array.Sort(arr);
         Array.Reverse(arr);
        return arr.OrderByDescending(x => x).ToArray();
    }

    public static int[] MergeArrays(int[] arr1, int[] arr2)
    {
        if (arr1 == null && arr2 == null)
        {
            return new int[0]; 
        }
        if (arr1 == null)
        {
            return (int[])arr2.Clone(); 
        }
        if (arr2 == null)
        {
            return (int[])arr1.Clone();
        }

        
        return arr1.Concat(arr2).ToArray();

        int[] mergedArray = new int[arr1.Length + arr2.Length];
        Array.Copy(arr1, 0, mergedArray, 0, arr1.Length);
        Array.Copy(arr2, 0, mergedArray, arr1.Length, arr2.Length);
        return mergedArray;
        
    }

    public static void Main(string[] args)
    {
        int[] numbers1 = { 5, 2, 8, 1, 9 };
        int[] numbers2 = { 7, 3, 6, 4 };

        Console.WriteLine(" Операции с массивами ");

        int[] sortedAsc = SortAscending((int[])numbers1.Clone()); 
        Console.WriteLine("Массив 1 (по возрастанию): " + string.Join(", ", sortedAsc)); 

        int[] sortedDesc = SortDescending((int[])numbers1.Clone());
        Console.WriteLine("Массив 2 (по убыванию): " + string.Join(", ", sortedDesc)); 
        int[] merged = MergeArrays(numbers1, numbers2);
        Console.WriteLine("Объединенный массив: " + string.Join(", ", merged)); 

        Console.WriteLine("\nНажмите любую клавишу для продолжения...");
        Console.ReadKey();
    }
}
