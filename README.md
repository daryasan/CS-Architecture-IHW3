# АВС, ИДЗ-3, Судакова Дарья, БПИ227, вариант 3
Задание выполнено на оценку 10.
## Условие
Разработать программу, находящую в заданной ASCII–строке первую слева направо последовательность N символов, каждый элемент которой определяется по условию «меньше предшествующего» (N
вводится как отдельный параметр). Понятие «меньше предшествующего» определяется в соответствии с порядком следования символов от начала строки.
### Замечания
1. В данном случае символ считается меньше предыдущего, если его код в таблице ASCII меньше кода предыдущего символа.
2. В случае, если с клавиатуры задано число большее, чем длина исходной строки, программа выдает сообщение об ошибке. Аналогично обрабатывается ввод нуля. В случае, если введена единица, программа выводит первый символ строки, поскольку он является первой встреченной убывающей последовательностью заданной длины 1.
3. В случае, если в исходной строке нет убывающей последовательности **ровно** из N символов (то есть если существует последовательность меньшего размера или ее не существует) на экран выводится сообщение о том, что такая последовательность не найдена.
## Критерии
### На оценку 4-5
0. Для запуска программы из main необходима следующая конфигурация файлов в rars:
   
    ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/526b483c-605c-4de3-9913-a54f04cd7951)

1. В данном репозитории приведено решение программы на ассемблере. Программа читает данные из файла. Результаты записываются в другой файл (папки tests и outputs).
2. Все изменяемые параметры программы вводятся с консоли.
   
    ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/84c5024c-a095-43b5-a963-98f9d647b72f)
   
3. В программе присутствуют комментарии, поясняющие выполняемые ей действия.  
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/94a8ff3f-7c78-4bcb-950d-9df7842b9ff3)

     
4. Обработка данных, полученных из файла сформирована в виде отдельной подпрограммы в файле [search_descending_sequence.asm](search_descending_sequence.asm).
5. В подкаталоге [tests](\tests) присутствуют файлы, используемые для тестирования.
6. Буфер для ввода текста динамически расширяется в зависимости от длины файла ([read_file.asm](read_file.asm)), каждая "порция" буфера имеет размер 512 байт.
   
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/76c60c44-8b43-4276-958d-6f7eb7b6609c)

### На оценку 6-7
1. Внутри функций необходимо используются переменные временных регистров, поскольку переменных не так много, и нет необходимости задействовать стек.
   
     ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/812c54bb-2c9f-43d9-970a-0b7a1b333973)
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/374c374d-488e-43aa-950f-197352966039)


2. Для чтения текста из файла реализован буфер ограниченного размера, равного 512 байтам, благодаря чему программа может читать большие файлы. Логика чтения описана в подпрограмме [read_file](read_file.asm)
3. Ввод данных, обработка и их вывод организованы с помощью подпрограмм [read_file](read_file.asm), [search_descending_sequence](search_descending_sequence.asm) и [write_to_file](write_to_file.asm) соответственно. Для передачи параметров используются регистры a0-a2, как и для возврата значений.

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/c1680f4a-2850-4d45-879a-ef91982c2212)
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/d803b514-4131-43b4-8ed8-5618c23787ba)
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/741f5998-a962-4b67-9ac4-f5909b1d3b43)


### На оценку 8
1. Добавлена возможность дополнительного вывода результатов на консоль. Выводить или нет решает пользователь отвечая «Y» или «N» на соответствующий вопрос компьютерной программы, при вводе других символом программа запрашивает ответ снова. Вывод программы при этом полностью соответствует выводу результатов в файл, поскольку найденная последовательность сначала записывается в файл, а потом та же самая строка выводится на консоль.

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/4e3267a3-cf54-4cd1-a3f6-baf3ebb6cffb)
   
   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/31c19218-6182-4dfc-8558-63cae2e5f033)

3. Реализована [тестовая программа](test_subprogramm), выполняющая многократный вызов открытия 4 тестовых файлов из папки tests, нахождения в каждом из них последовательностей различной длины, вывода их на экран и записи одной из них в файл в папке outputs. Для корректной работы данной подпрограммы необходима следующая конфигурация флагов в rars:

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/41f39d7b-19a4-4962-a23c-2e78d9ae1179)

Вывод программы выглядит следующим образом:  

![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/a59ff118-c395-435f-83f2-f0091bf32a14)  
![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/35478c50-c2f2-4e5c-aa42-fb9dfadb6afe)


### На оценку 9
1. В программу добавлены макросы, которые вынесены в отдельную библиотеку [macros.asm](macros.asm). В комментариях указано назначение макроса и параметры:

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/4419d772-6749-478a-a498-8db350f1703c)

Некоторые макросы вызывают соответствующие подпрограммы:  

![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/38a2c197-c1c9-4f1d-a94a-4c2719f960b2)  

2. Добавлена еще одна тестовая подпрограмма [test_macros.asm](test_macros.asm). Для ее корректного запуска нужны такое же флаги, как и для первой тестовой подпрограммы, ее вывод выглядит следующим образом:

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/3d80e5b2-9f7c-4dff-b517-274dd7be2e02)

Данная подпрограмма использует 6 тестовых файлов из папки tests, и выводит на экран последовательности для разных значений N для каждого из файлов.

### На оценку 10
1. Программа разделена на подпрограммы, каждая из которых вынесена в отдельный файл. ДЛя сборки используется директива .global, флаги для эмулятора указаны в пункте 0 в начале отчета.

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/3c72bc96-b49f-426a-928b-e748917f4f13)

2. Макросы вынесены в отдельную библиотеку [macros.asm](macros.asm).
3. Использованы отдельные графические окна эмулятора, которые выглядят так:

   ![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/4dbe4355-2e1c-4eb2-8876-d09bbdc55ae1)

За них отвечает флаг popup dialog for input syscalls.

## Конец отчета!  
![image](https://github.com/DaryaAutumn/CS-Architecture-IHW3/assets/72216853/9666ccf1-ce34-4d01-be82-fffcf75ce1c9)



