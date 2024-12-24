# FaleReading
static void Main()
    {
        string filePath = "C:\\Users\\revno\\COPYFILE\\24_demo.txt"; //Путь к файлу
        try
        {
            string content = File.ReadAllText(filePath); //Чтение текста в файле
            int maxLength = FindLongestXSequence(content); //Использование метода и запись результата
            Console.WriteLine($"Самая длинная последовательность из 'X': {maxLength}");
        }
        catch (Exception ex) //Обработчик исключений
        {
            Console.WriteLine($"Ошибочка: {ex.Message}");
        }
    }

    static int FindLongestXSequence(string str) //Метод для поиска X в тексте
    {
        int maxCount = 0; // Максимальная длина последовательности
        int currentCount = 0; //Переменная счетчика

        foreach (char c in str)
        {
            if (c == 'X') //Поиск символов X в тексте
            {
                currentCount++; //Увеличение счетчика
            }
            else
            {
                if (currentCount > maxCount) //Проверка соответствия
                {
                    maxCount = currentCount; //Перенос значения счетчика в длинну последовательности
                }
                currentCount = 0; // Сброс счетчика
            }
        }

        // Проверка последней последовательности
        if (currentCount > maxCount)
        {
            maxCount = currentCount;
        }

        return maxCount;
    }
}
