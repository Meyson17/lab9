
<h2 align="center">ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ПРОФЕССИОНАЛЬНОГО ОБРАЗОВАНИЯ <br> «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ» <br> КАФЕДРА ИНФОРМАТИКИ </h2>
<p align="center">Лабораторная работа №9 <br>
по курсу «Web-технологии, языки и средства создания web-приложений» 

<p align="center"><b>"Java Script"</b><p>
<p align="right"><b>Выполнил: </b> студент 231 группы Рыжков Владимир</p>
<p  align="right"><b>Принял: </b> Соболев Е. И., старший преподователь</p>
<br>
<br>
<br>
<p align="center">Южно-Сахалинск <br> СахГУ <br> 2023</p>
<h2> Введение </h2>
<p>Лабораторные работы по дисциплине «Web-технологии, языки и средства создания web-приложений» предназначены для освоения полученных теоретических знаний на практике. Цель работы - выполнить задачи, написав решение на Java Script:  <br>
<ol>
   <li> Есть некоторая строка (var str = 'fgfggg';), что будет, если мы возьмем str[0]?
   <li>Дана функция, она принимает в качестве аргументов строки '*', '1', 'b', '1c', реализуйте ее так, что бы она вернула строку '1*b*1c'
     <li>Дано дерево, надо найти сумму всех вершин.
       <li>Нарисовать стилями полукруг.
         <li>Есть массив в котором лежат объекты с датами, отсортировать по датам.
           <li>Есть несколько слов, определить состоят ли они из одних и тех же букв('кот', 'ток', 'окт')
             <li>От них же. Числа от 1 до 100 лежат в массиве, они хаотично перемешанные, от туда изъяли одно число, надо найти, что это за число. алгоритм не должен превышать O(n^2) сложности.
               <li>Реализовать сортировку пузырьком.
                 <li>Обратная польская нотация.
                   <li>Реализовать функцию является ли слово палендром.
   </ol>
Для реализации данной работы будет использоваться Notepad++. Выполнение кода будет происходить в браузере Microsoft Edge.
</p>
<h2>Решение задач</h2>
<code>
      
     //1
    function num1()
    {
    var str = 'fgfggg';
    console.log(str[0]);
    }
    function cb(str1, str2, str3, str4)
    {
    return str2 + str1 + str3 + str1 + str4;
    }

	  //2
    function num2()
    {
    console.log(cb('*','1','b','1c'));
    }
    
	  //3
    function num3()
    {
    class Node {
        constructor(value, children) {
            this.value = value;
            this.children = children || [];
        }
    }

    function sumNodes(root) {
        let sum = 0;
        if (!root) {
            return sum;
        }
        sum += root.value;
        for (let child of root.children) {
            sum += sumNodes(child);
        }
        return sum;
    }

    // Пример использования:
    let tree = new Node(1, [
        new Node(2, [new Node(4)]),
        new Node(3, [new Node(5), new Node(6)])
    ]);

    console.log(sumNodes(tree)); // 21
    }
    
	  //4
    function num4()
    {
    let style = "<style>\ndiv{\nborder: 2px solid black;\nbackground-color: green;\nborder-radius: 100% 0 0 100% / 50% 0 0 50%;\nwidth: 100px;\nheight: 200px;\n}\n</style>\n<div></div>";
    document.write(style)
    }
    
	  //5
    function num5()
    { 
    let array = [new Date('1.1.2023'), new Date('3.3.2020'), new Date('2.2.2019'), new Date('4.4.2023')];
    
    for(let i = 0; i < array.length; i++)
    {
        for(let j = i + 1; j < array.length; j++)
        {
            if (array[j].getTime() < array[i].getTime())
                {
                    let temp = array[i];
                    array[i] = array[j];
                    array[j] = temp;
                }
        }
    }

    for(let i = 0; i < array.length; i++)
    {
        console.log(array[i].toString());  
    }
    }

    function equals(str1, str2, str3)
    {
    let temp = [];
    for(let i = 0; i < str1.length; i++)
    {
        if(!temp.includes(str1[i]))
            temp.push(str1[i])
    }

    for(let i = 0, j = 0; i != str2.length-1 || j != str3.length -1; )
    {
        if(!temp.includes(str2[i]) || !temp.includes(str3[j]) )
            return false;
        if( i + 1 != str2.length) i++;
        if( j + 1 != str3.length) j++;
    }
    return true;
    }
    
	  //6
    function num6()  
    {
    console.log(equals('ктоо','ктто','ктототкто'));
    }


    function ot(array)
    {
    let one = 0;
    let two = 0;
    for(let i = 1; i <= 100; i++) one += i;
    for(let i = 0; i < array.length; i++) two += array[i];
    return one - two;
    }
    
	  //7
    function num7()
    {
    let input = [];
    let num = Math.floor(Math.random() * 100);
    for(let i = 100; i > 0; i--) 
    {
        if(i != num)
            input.push(i);
        else
            console.log(i)
    }
    console.log(ot(input));
    }

    function bubble(array)
    {
    for(let i = 0; i < array.length; i++)
    {
        for(let j = i + 1; j < array.length; j++)
            if(array[j] < array[i])
            {
                let temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
    }
    return array;
    }
    
	  //8
    function num8()
    {
    let test = [3,4,2,1,6,8,9,5,7]
    console.log(bubble(test));
    }

    function polishNotation(str)
    {
    let temp = str.split(' ');
    let operands = [];
    for(let i = 0; i < temp.length; i++)
    {
        switch(temp[i])
        {
            case "+":
                let sum = 0;
                for(let j = 0; j < operands.length; j++)
                    sum += operands[j];
                operands = [sum];
                break;
            case "-":
                let dif = operands[0];
                for(let j = 1; j < operands.length; j++)
                    dif -= operands[j];
                operands = [dif];
                break;
            case "*":
                let mult = 1;
                for(let j = 0; j < operands.length; j++)
                    mult *= operands[j];
                operands = [mult];
                break;
            case "/":
                let div = operands[0];
                for(let j = 1; j < operands.length; j++)
                {
                    if(operands[j] != 0)
                        div /= operands[j];
                }
                operands = [div];
                break;
            default:
                operands.push(parseInt(temp[i]));
                break;
        }
    }
    return operands[0];
    }
    
	  //9
    function num9()
    {
    console.log(polishNotation("1 2 + 4 * 3 +"));
    }

    function isPolendrom(str)
    {
    str = str.toLowerCase();
    str = str.replaceAll(" ");
    for(let i = 0; i < Math.floor(str.length / 2); i++)
    {
       if(str[i] != str[str.length - (i+1)])
            return false;
    }
    return true;
    }
    
	  //10
    function num10()
    {
    console.log(isPolendrom(prompt("Input string")));
    }
</code>
<h2>Вывод</h2>
<p>В ходе лабораторной работы были изучены элементы языка Java script. Были рассмотрены способы задания переменных, операций над ними, была проведена работа с циклами и функциями. Результатом лабораторной работы является сайт с решенными задачами.</p>    
