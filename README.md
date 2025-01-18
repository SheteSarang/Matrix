using System;

class MatrixOperations
{
    // Hardcoded matrices
    static int[,] matrix1 = {
        { 1, 2, 3 },
        { 4, 5, 6 },
        { 7, 8, 9 }
    };

    static int[,] matrix2 = {
        { 9, 8, 7 },
        { 6, 5, 4 },
        { 3, 2, 1 }
    };

    // Matrix Addition
    public static int[,] AddMatrices(int[,] matrix1, int[,] matrix2)
    {
        int rows = matrix1.GetLength(0);
        int cols = matrix1.GetLength(1);
        int[,] result = new int[rows, cols];
        
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                result[i, j] = matrix1[i, j] + matrix2[i, j];
            }
        }
        return result;
    }

    // Matrix Subtraction
    public static int[,] SubtractMatrices(int[,] matrix1, int[,] matrix2)
    {
        int rows = matrix1.GetLength(0);
        int cols = matrix1.GetLength(1);
        int[,] result = new int[rows, cols];
        
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                result[i, j] = matrix1[i, j] - matrix2[i, j];
            }
        }
        return result;
    }

    // Matrix Multiplication
    public static int[,] MultiplyMatrices(int[,] matrix1, int[,] matrix2)
    {
        int rows1 = matrix1.GetLength(0);
        int cols1 = matrix1.GetLength(1);
        int rows2 = matrix2.GetLength(0);
        int cols2 = matrix2.GetLength(1);
        
        if (cols1 != rows2)
            throw new InvalidOperationException("Matrix dimensions are not compatible for multiplication.");
        
        int[,] result = new int[rows1, cols2];
        
        for (int i = 0; i < rows1; i++)
        {
            for (int j = 0; j < cols2; j++)
            {
                result[i, j] = 0;
                for (int k = 0; k < cols1; k++)
                {
                    result[i, j] += matrix1[i, k] * matrix2[k, j];
                }
            }
        }
        return result;
    }

    // Matrix Transpose
    public static int[,] TransposeMatrix(int[,] matrix)
    {
        int rows = matrix.GetLength(0);
        int cols = matrix.GetLength(1);
        int[,] result = new int[cols, rows];
        
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                result[j, i] = matrix[i, j];
            }
        }
        return result;
    }

    // Print Matrix
    public static void PrintMatrix(int[,] matrix)
    {
        int rows = matrix.GetLength(0);
        int cols = matrix.GetLength(1);
        
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                Console.Write(matrix[i, j] + " ");
            }
            Console.WriteLine();
        }
    }

    static void Main(string[] args)
    {
        Console.WriteLine("Matrix 1:");
        PrintMatrix(matrix1);
        
        Console.WriteLine("\nMatrix 2:");
        PrintMatrix(matrix2);
        
        // Matrix Addition
        var sum = AddMatrices(matrix1, matrix2);
        Console.WriteLine("\nMatrix Addition:");
        PrintMatrix(sum);
        
        // Matrix Subtraction
        var difference = SubtractMatrices(matrix1, matrix2);
        Console.WriteLine("\nMatrix Subtraction:");
        PrintMatrix(difference);
        
        // Matrix Multiplication
        var product = MultiplyMatrices(matrix1, matrix2);
        Console.WriteLine("\nMatrix Multiplication:");
        PrintMatrix(product);
        
        // Matrix Transpose
        var transpose1 = TransposeMatrix(matrix1);
        Console.WriteLine("\nTranspose of Matrix 1:");
        PrintMatrix(transpose1);
        
        var transpose2 = TransposeMatrix(matrix2);
        Console.WriteLine("\nTranspose of Matrix 2:");
        PrintMatrix(transpose2);
    }
}
