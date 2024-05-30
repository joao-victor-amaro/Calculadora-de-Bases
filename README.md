# Calculadora-de-Bases
Primeiro trabalho pratico da faculdade uma calculadora de conversão de bases em C#

using System.Collections.Generic;
using System.Linq;
using System;
using System.Security.Cryptography;

internal class Program
{
    private static void Main(string[] args)
    {
        Menu();

    }

    /*static void Opcao1()
    {


        int resto, quociente;
        List<int> resultado = [];
        Console.WriteLine("Decimal --> Binário");
        Console.WriteLine("Digite um número decimal para ser convertido para binário: ");
        int numero;
        bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out numero);
        

        if (validacaoDoDigito == false)
        {
            Console.WriteLine("Digito inválido. Por favor, insira um numero decimal válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao1();
        }

        Console.WriteLine("|------------------------------------------------------------------|");

        quociente = numero / 2;
        resto = numero % 2;

        Console.WriteLine($"Primeiro passo: {numero} / 2 -> Quociente: {quociente}, Resto: {resto}");

        resultado.Add(resto);
        do
        {
            int passos = quociente;
            resto = quociente % 2;
            quociente /= 2;
            resultado.Add(resto);

            Console.WriteLine($"Próximo passo: {passos} / 2 -> Quociente: {quociente}, Resto: {resto}");


        } while (quociente > 0);

        resultado.Reverse();

        foreach (int i in resultado)
        {

            Console.Write(i);

        }
        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }*/

    static void Opcao2()
    {
        Console.WriteLine("Binário --> Decimal \n");
        Console.WriteLine("Digite um número binário para ser convertido para decimal: ");
        int binario;
        bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out binario);

        if (validacaoDoDigito == false)
        {
            Console.WriteLine("Digito inválido. Por favor, insira um numero Binário válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao2();
        }

        string inverso = new string(binario.ToString().Reverse().ToArray());

        if (string.IsNullOrEmpty(inverso) || !inverso.All(c => c == '0' || c == '1'))
        {
            Console.WriteLine("Número inválido. Por favor, insira um número binário válido.");
            Console.WriteLine("Aperte enter para inserir outro numero!");
            Console.ReadKey();
            Opcao2();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        double soma = 0;
        double posicao = 0;
        int numeroconvertido;
        double somafinal = 0;

        for (int i = 0; i < inverso.Length; i++)
        {

            numeroconvertido = int.Parse(inverso.Substring(i, 1));
            int calculo = (int)Math.Pow(2, posicao);
            soma = numeroconvertido * calculo;
            posicao++;
            somafinal += (soma = numeroconvertido * calculo);
            Console.WriteLine($"Soma atual: {numeroconvertido} = {numeroconvertido} * {calculo} = {soma}");
        }
        Console.WriteLine("O número convertido é: " + somafinal);
        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }

    /* static void Opcao3()
     {
         List<int> resultado = [];
         int resto, quociente;
         Console.WriteLine("Decimal --> Octal");
         Console.WriteLine("Digite um número decimal para ser convertido para octal: ");
         int numero;
         bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out numero);


         if (validacaoDoDigito == false)
         {
             Console.WriteLine("Digito inválido. Por favor, insira um numero decimal válido.");
             Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
             Console.ReadKey();
             Console.Clear();
             Opcao3();
         }
         Console.WriteLine("|------------------------------------------------------------------|");
         quociente = numero / 8;
         resto = numero % 8;

         resultado.Add(resto);

         Console.WriteLine($"Primeiro passo: {numero} / 8 -> Quociente: {quociente}, Resto: {resto}");

         do
         {
             int passos = quociente;
             resto = quociente % 8;
             quociente /= 8;
             resultado.Add(resto);

             Console.WriteLine($"Próximo passo: {passos} / 8 -> Quociente: {quociente}, Resto: {resto}");
         } while (quociente >= 1);

         resultado.Reverse();

         foreach (int i in resultado)
         {
             Console.Write(i);
         }
         Console.WriteLine("\n");
         Console.WriteLine("Aperte enter para voltar pro Menu! ");
         Console.ReadKey();
         Console.Clear();
         Menu();
     }*/

    static void Opcao4()
    {
        Console.WriteLine("Octal --> Decimal");
        Console.WriteLine("Digite um número octal para ser convertido para decimal: ");
        int numero;
        bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out numero);

        if (validacaoDoDigito == false)
        {
            Console.WriteLine("Digito inválido. Por favor, insira um numero octal válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao4();
        }

        string inverso = new string(numero.ToString().Reverse().ToArray());

        if (string.IsNullOrEmpty(inverso) || !inverso.All(c => c >= '0' && c <= '7'))
        {
            Console.WriteLine("Esse numero eh inválido. Digite um número em octal.");
            Console.WriteLine("Aperte enter para inserir outro numero!");
            Console.ReadKey();
            Console.Clear();
            Opcao4();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        double soma = 0;
        double posicao = 0;
        int numeroconvertido;
        double somafinal = 0;

        for (int i = 0; i < inverso.Length; i++)
        {

            numeroconvertido = int.Parse(inverso.Substring(i, 1));
            int calculo = (int)Math.Pow(8, posicao);
            soma = numeroconvertido * calculo;
            posicao++;
            somafinal += (soma = numeroconvertido * calculo);
            Console.WriteLine($"Soma atual: {numeroconvertido} = {numeroconvertido} * {calculo} = {soma}");
        }
        Console.WriteLine("O número convertido é: " + somafinal);
        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }

    static void Opcao5()
    {
        int contador = 1;
        int resto, quociente = 1;
        string hex = "";
        Console.WriteLine("Decimal --> Hexadecimal");
        Console.WriteLine("Digite um número decimal para ser convertido para hexadecimal: ");
        int numero;
        bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out numero);

        if (validacaoDoDigito == false)
        {
            Console.WriteLine("Digito inválido. Por favor, insira um numero decimal binário válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao5();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        while (quociente != 0)
        {



            quociente = numero / 16;
            resto = numero % 16;

            if (resto <= 9)
            {
                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {resto}");

                hex += resto;
            }

            else if (resto == 10)
            {
                char letra = 'A';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 11)
            {
                char letra = 'B';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 12)
            {
                char letra = 'C';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 13)
            {
                char letra = 'D';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 14)
            {
                char letra = 'E';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 15)
            {
                char letra = 'F';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            numero = quociente;

            contador++;


        }


        string numeroinvertido = new string(hex.ToString().Reverse().ToArray());

        Console.Write("Resultado: " + numeroinvertido);



        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }

    static void Opcao6()
    {
        Console.WriteLine("Hexadecimal --> Decimal");
        Console.WriteLine("Informe um número hexadecimal para ser convertido para decimal: ");
        string numero = Console.ReadLine().ToUpper();

        if (string.IsNullOrEmpty(numero) || !numero.All(c => (c >= '0' && c <= '9') || (c >= 'A' && c <= 'F')))
        {
            Console.WriteLine("Número inválido. Por favor, insira um número hexadecimal válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao6();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        double soma = 0;
        string valoresMultiplicacao = "";

        for (int i = 0; i < numero.Length; i++)
        {
            char hexaChar = numero[numero.Length - 1 - i];
            int numDec;

            switch (hexaChar)
            {
                case 'A':
                    numDec = 10;
                    break;
                case 'B':
                    numDec = 11;
                    break;
                case 'C':
                    numDec = 12;
                    break;
                case 'D':
                    numDec = 13;
                    break;
                case 'E':
                    numDec = 14;
                    break;
                case 'F':
                    numDec = 15;
                    break;
                default:
                    numDec = Convert.ToInt32(hexaChar.ToString());
                    break;
            }

            double valorMultiplicado = numDec * Math.Pow(16, i);
            Console.WriteLine($"{numDec} * 16 ^ {i} = {valorMultiplicado}");
            soma += valorMultiplicado;

            valoresMultiplicacao += valorMultiplicado;
            if (i < numero.Length - 1)
            {
                valoresMultiplicacao += " + ";
            }
        }

        Console.WriteLine($"\n{valoresMultiplicacao} = {soma}");
        Console.WriteLine($"\nO valor decimal do número hexadecimal {numero} é: {soma}\n");

        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }


    static void Opcao7()
    {
        string numero, temp, numbinario = "", octal = "";
        int count = 0;
        Console.WriteLine("Binário --> Octal");
        Console.WriteLine("Insira um número binário para ser convertido em octal: ");
        numero = Console.ReadLine();
        int num = Convert.ToInt32(numero);

        if (string.IsNullOrEmpty(numero) || !numero.All(c => c == '0' || c == '1'))
        {
            Console.WriteLine("Digito invalido. Digite um número binário válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao7();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        for (int i = 0; i <= numero.Length - 1; i++)
        {
            count = count + 1;
            if (count == 3)
            {
                count = 0;
            }
        }
        temp = numero;
        if (count == 1)
        {
            numero = "00" + temp;
        }
        if (count == 2)
        {

            numero = "0" + temp;
        }

        for (int i = 0; i <= numero.Length - 1; i++)
        {
            numbinario += numero.Substring(i, 1);


            if (numbinario.Length == 3)
            {
                octal += FunçãoOctal(numbinario);

                numbinario = "";

            }



        }



        Console.WriteLine("\n");
        Console.WriteLine("Resultado é " + octal);

        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }

    static string FunçãoOctal(string converter)
    {
        string valor = "";
        switch (converter)
        {
            case "000":
                valor = "0";
                Console.Write("0 = 000 ");
                break;
            case "001":
                valor = "1";
                Console.Write("1 = 001 ");
                break;
            case "010":
                valor = "2";
                Console.Write("2 = 010 ");
                break;
            case "011":
                valor = "3";
                Console.Write("3 = 011 ");
                break;
            case "100":
                valor = "4";
                Console.Write("4 = 100 ");
                break;
            case "101":
                valor = "5";
                Console.Write("5 = 101 ");
                break;
            case "110":
                valor = "6";
                Console.Write("6 = 110 ");
                break;
            case "111":
                valor = "7";
                Console.Write("7 = 111 ");
                break;
            default:
                break;
        }
        return valor;
    }

    static void Opcao8()
    {
        Console.WriteLine("Octal --> Binário");
        Console.WriteLine("Insira um número octal para conversão em binário: ");
        string octal = Console.ReadLine();

        if (string.IsNullOrEmpty(octal) || !octal.All(c => c >= '0' && c <= '7'))
        {
            Console.WriteLine("Digito inválido. Digite um número em octal.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao8();
        }
        Console.WriteLine("|------------------------------------------------------------------|");

        Console.WriteLine("Troque os valores de cada numero pelo seu correspondente binario. ");
        string[] vetor = { "000", "001", "010", "011", "100", "101", "110", "111" };


        string binario = "";

        foreach (char digito in octal)
        {

            int digitoctal = int.Parse(digito.ToString());
            string digitobinario = vetor[digitoctal];
            Console.Write($"{digito} =  {digitobinario} ");

            binario = binario + digitobinario;
        }

        Console.WriteLine("\nO número binário correspondente é: " + binario);

        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();

    }

    static void Opcao9()
    {
        string numero, temp, numbinario = "", hexadecimal = "", conta = "";
        int count = 0;
        Console.WriteLine("Binário --> Hexadecimal");
        Console.WriteLine("Insira o número binário para ser convertido em hexadecimal: ");
        numero = Console.ReadLine();

        if (string.IsNullOrEmpty(numero) || !numero.All(c => c == '0' || c == '1'))
        {
            Console.WriteLine("Número inválido. Por favor, insira um número binário válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao9();
        }

        Console.WriteLine("|------------------------------------------------------------------|");
        for (int i = 0; i <= numero.Length - 1; i++)
        {
            count += 1;
            if (count == 4)
            {
                count = 0;
            }
        }
        temp = numero;
        if (count == 1)
        {
            numero = "000" + temp;
        }
        if (count == 2)
        {
            numero = "00" + temp;
        }
        if (count == 3)
        {
            numero = "0" + temp;
        }

        for (int i = 0; i <= numero.Length - 1; i++)
        {
            numbinario += numero.Substring(i, 1);
            if (numbinario.Length == 4)
            {
                hexadecimal += FunçãoHexadecimal(numbinario);
                numbinario = "";
            }
        }

        Console.WriteLine("Resultado é " + hexadecimal);

        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();




    }
    static string FunçãoHexadecimal(string converter)
    {
        string valor = "";
        switch (converter)
        {
            case "0000":
                valor = "0";
                break;
            case "0001":
                valor = "1";
                break;
            case "0010":
                valor = "2";
                break;
            case "0011":
                valor = "3";
                break;
            case "0100":
                valor = "4";
                break;
            case "0101":
                valor = "5";
                break;
            case "0110":
                valor = "6";
                break;
            case "0111":
                valor = "7";
                break;
            case "1000":
                valor = "8";
                break;
            case "1001":
                valor = "9";
                break;
            case "1010":
                valor = "A";
                break;
            case "1011":
                valor = "B";
                break;
            case "1100":
                valor = "C";
                break;
            case "1101":
                valor = "D";
                break;
            case "1110":
                valor = "E";
                break;
            case "1111":
                valor = "F";
                break;
            default:
                break;
        }
        return valor;

    }

    static void Opcao10()
    {
        string hexadecimal = "", numero;
        Console.WriteLine("Hexadecimal --> Binário");
        Console.WriteLine("Insira um número hexadecimal para conversão em binário: ");
        numero = Console.ReadLine().ToUpper();

        if (string.IsNullOrEmpty(numero) || !numero.All(c => (c >= '0' && c <= '9') || (c >= 'A' && c <= 'F')))
        {
            Console.WriteLine("Número inválido. Digite um número hexadecimal válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao10();
        }
        Console.WriteLine("|------------------------------------------------------------------|");
        for (int i = 0; i < numero.Length; i++)
        {
            switch (numero.Substring(i, 1))
            {
                case "0":
                    hexadecimal += "0000";
                    Console.Write("0 = 0000 ");
                    break;
                case "1":
                    hexadecimal += "0001";
                    Console.Write("1 = 0001 ");
                    break;
                case "2":
                    hexadecimal += "0010";
                    Console.Write("2 = 0010 ");
                    break;
                case "3":
                    hexadecimal += "0011";
                    Console.Write("2 = 0011 ");
                    break;
                case "4":
                    hexadecimal += "0100";
                    Console.Write("4 = 0100 ");
                    break;
                case "5":
                    hexadecimal += "0101";
                    Console.Write("5 = 0101 ");
                    break;
                case "6":
                    hexadecimal += "0110";
                    Console.Write("6 = 0110 ");
                    break;
                case "7":
                    hexadecimal += "0111";
                    Console.Write("7 = 0111 ");
                    break;
                case "8":
                    hexadecimal += "1000";
                    Console.Write("8 = 1000 ");
                    break;
                case "9":
                    hexadecimal += "1001";
                    Console.Write("9 = 1001 ");
                    break;
                case "A":
                    hexadecimal += "1010";
                    Console.Write("A = 1010 ");
                    break;
                case "B":
                    hexadecimal += "1011";
                    Console.Write("B = 1011 ");
                    break;
                case "C":
                    hexadecimal += "1100";
                    Console.Write("C = 1100 ");
                    break;
                case "D":
                    hexadecimal += "1101";
                    Console.Write("D = 1101 ");
                    break;
                case "E":
                    hexadecimal += "1110";
                    Console.Write("E = 1110 ");
                    break;
                case "F":
                    hexadecimal += "1111";
                    Console.Write("F = 1111 ");
                    break;
            }

        }
        Console.Write("O resultado é: " + hexadecimal);

        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();

    }

    static void Opcao11()
    {
        Console.WriteLine("Octal --> Hexadecimal");
        Console.WriteLine("Digite um número octal para ser convertido para hexadecimal: ");
        string octal = Console.ReadLine();

        if (string.IsNullOrEmpty(octal) || !octal.All(c => c >= '0' && c <= '7'))
        {
            Console.WriteLine("Esse numero eh inválido. Digite um número em octal.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao11();
        }

        Console.WriteLine("|------------------------------------------------------------------|");

        int dec = 0;

        int remin = Convert.ToInt32(octal);
        int i = 0;


        Console.WriteLine("Primeiro o número sera passado octal para decimal, depois para hexadecimal");

        while (remin > 0)
        {
            dec += remin % 10 * (int)Math.Pow(8, i);
            remin /= 10;
            i++;
            int contadorOctal = 1;
            contadorOctal++;
            Console.WriteLine($"Primeiro {contadorOctal}: {octal} / 16 -> Quociente: {remin}, Resto: {dec}");

        }


        Console.WriteLine("O numero em octal " + octal + " eh passado para deciamal " + dec);
        Console.WriteLine();

        int contador = 1;
        int resto, quociente = 1;
        string hex = "";

        int numero = dec;
        Console.WriteLine("|------------------------------------------------------------------|");

        while (quociente != 0)
        {



            quociente = numero / 16;
            resto = numero % 16;

            if (resto <= 9)
            {
                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {resto}");

                hex += resto;
            }

            else if (resto == 10)
            {
                char letra = 'A';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 11)
            {
                char letra = 'B';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 12)
            {
                char letra = 'C';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 13)
            {
                char letra = 'D';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 14)
            {
                char letra = 'E';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            else if (resto == 15)
            {
                char letra = 'F';

                hex += letra;

                Console.WriteLine($"Primeiro {contador}: {numero} / 16 -> Quociente: {quociente}, Resto: {letra}");
            }

            numero = quociente;

            contador++;


        }


        Console.Write("Resultado: " + hex);



        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();
    }

    static void Opcao12()
    {
        Console.WriteLine("hexadecimal --> Octal");
        Console.WriteLine("Informe um número hexadecimal para ser convertido para octal: ");
        string numero = Console.ReadLine().ToUpper();

        if (string.IsNullOrEmpty(numero) || !numero.All(c => (c >= '0' && c <= '9') || (c >= 'A' && c <= 'F')))
        {
            Console.WriteLine("Número inválido. Por favor, insira um número hexadecimal válido.");
            Console.WriteLine("Aperte enter para voltar para inserir outro numero! ");
            Console.ReadKey();
            Console.Clear();
            Opcao12();
        }

        Console.WriteLine("|------------------------------------------------------------------|");

        double soma = 0;
        string valoresMultiplicacao = "";

        for (int i = 0; i < numero.Length; i++)
        {
            char hexaChar = numero[numero.Length - 1 - i];
            int numDec;

            switch (hexaChar)
            {
                case 'A':
                    numDec = 10;
                    break;
                case 'B':
                    numDec = 11;
                    break;
                case 'C':
                    numDec = 12;
                    break;
                case 'D':
                    numDec = 13;
                    break;
                case 'E':
                    numDec = 14;
                    break;
                case 'F':
                    numDec = 15;
                    break;
                default:
                    numDec = Convert.ToInt32(hexaChar.ToString());
                    break;
            }

            double valorMultiplicado = numDec * Math.Pow(16, i);
            Console.WriteLine($"{numDec} * 16 ^ {i} = {valorMultiplicado}");
            soma += valorMultiplicado;

            valoresMultiplicacao += valorMultiplicado;
            if (i < numero.Length - 1)
            {
                valoresMultiplicacao += " + ";
            }
        }

        Console.WriteLine($"\n{valoresMultiplicacao} = {soma}");
        Console.WriteLine($"\nO valor decimal do número hexadecimal {numero} é: {soma}\n");


        Console.WriteLine("\n");
        Console.WriteLine("Aperte enter para voltar pro Menu! ");
        Console.ReadKey();
        Console.Clear();
        Menu();


    }

    static void OpcaoDeConversao(int escolha)
    {
        if (escolha <= 12 && escolha >= 0)
        {


            switch (escolha)
            {
                case 0:
                    Console.WriteLine("Programa encerrado");
                    break;

                case 1:

                    //Opcao1();
                    break;

                case 2:

                    Opcao2();
                    break;

                case 3:
                    //Opcao3();
                    break;

                case 4:
                    Opcao4();
                    break;

                case 5:
                    Opcao5();
                    break;

                case 6:
                    Opcao6();
                    break;

                case 7:
                    Opcao7();
                    break;

                case 8:
                    Opcao8();
                    break;

                case 9:
                    Opcao9();
                    break;

                case 10:
                    Opcao10();
                    break;

                case 11:
                    Opcao11();
                    break;

                case 12:
                    Opcao12();
                    break;

                default:
                    Console.Clear();
                    break;

            }

        }
        else
        {
            Console.WriteLine("Digite um núemro que tenha no Menu!");
            Console.WriteLine("Aperte enter para voltar pro Menu! ");
            Console.ReadKey();
            Console.Clear();
            Menu();
        }
    }

    static void Menu()
    {
        Console.WriteLine("Menu de conversão de base: ");
        Console.WriteLine("|------------------------------------------------------------------|");
        Console.WriteLine(" 1: Decimal --> Binário");
        Console.WriteLine(" 2: Binário --> Decimal");
        Console.WriteLine(" 3: Decimal --> Octal");
        Console.WriteLine(" 4: Octal --> Decimal");
        Console.WriteLine(" 5: Decimal --> Hexadecimal");
        Console.WriteLine(" 6: Hexadecimal --> Decimal");
        Console.WriteLine(" 7: Binário --> Octal");
        Console.WriteLine(" 8: Octal --> Binário");
        Console.WriteLine(" 9: Binário --> Hexadecimal");
        Console.WriteLine(" 10: Hexadecimal --> Binário");
        Console.WriteLine(" 11: Octal --> Hexadecimal");
        Console.WriteLine(" 12 hexadecimal --> Octal");
        Console.WriteLine("|------------------------------------------------------------------|");
        Console.WriteLine(" 0: Sair da calculadora");

        Console.WriteLine("Digite um número para fazer a conta: ");
        int escolha;
        bool validacaoDoDigito = int.TryParse(Console.ReadLine(), out escolha);

        if (validacaoDoDigito == false)
        {
            Console.WriteLine("Você digitou uma letra ou caracter inesperada");
            Console.WriteLine("Aperte enter para voltar pro Menu! ");
            Console.ReadKey();
            Console.Clear();
            Menu();
        }
        do
        {
            OpcaoDeConversao(escolha);

        } while (escolha != 0);
    }
}






