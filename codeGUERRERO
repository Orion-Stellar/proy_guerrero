using System;

class Programa
{
    static int fuerza = 10;
    static int resistencia = 10;
    static int energia = 20;
    static int experiencia = 0;
    static int nivel = 1;
    static Random random = new Random();

    static void Main()
    {
        int opcion;
        do
        {
            Console.WriteLine("==================================");
            Console.WriteLine("Guerrero del barrio - Menu principal");
            Console.WriteLine("1. Ver estado del guerrero");
            Console.WriteLine("2. Entrenar fuerza");
            Console.WriteLine("3. Entrenar resistencia");
            Console.WriteLine("4. Pelear");
            Console.WriteLine("5. Dormir");
            Console.WriteLine("6. Salir");
            Console.WriteLine("==================================");
            Console.Write("Elige tu destino: ");
            opcion = Convert.ToInt32(Console.ReadLine());

            switch (opcion)
            {
                case 1:
                    VerEstado();
                    break;
                case 2:
                    EntrenarFuerza();
                    break;
                case 3:
                    EntrenarResistencia();
                    break;
                case 4:
                    Pelear();
                    break;
                case 5:
                    Dormir();
                    break;
                case 6:
                    Console.WriteLine("El guerrero se fue a comer tacos, fin del juego");
                    break;
                default:
                    Console.WriteLine("Ese numero no existe, compa");
                    break;
            }
            SubirNivel();
        }
        while (opcion != 6);
    }

    static void VerEstado()
    {
        Console.WriteLine("----------");
        Console.WriteLine("Nivel: " + nivel);
        Console.WriteLine("Fuerza: " + fuerza);
        Console.WriteLine("Resistencia: " + resistencia);
        Console.WriteLine("Energia: " + energia);
        Console.WriteLine("Experiencia: " + experiencia);
        Console.WriteLine("----------");
    }

    static void EntrenarFuerza()
    {
        int maxHoras = energia / 5;
        if (maxHoras == 0)
        {
            Console.WriteLine("Estas tan cansado que apenas puedes levantar una cuchara");
            return;
        }

        Console.Write("Cuantas horas quieres entrenar fuerza? Maximo " + maxHoras + ": ");
        int opcion = Convert.ToInt32(Console.ReadLine());
        if (opcion > maxHoras) opcion = maxHoras;

        for (int i = 0; i < opcion; i++)
        {
            fuerza += 6;
            energia -= 5;
        }
        experiencia += 5;
        Console.WriteLine("Tu guerrero termino de levantar fierros como si le pagaran");
    }

    static void EntrenarResistencia()
    {
        int maxHoras = energia / 2;
        if (maxHoras == 0)
        {
            Console.WriteLine("Estas tan cansado que no aguantas ni una vuelta a la esquina");
            return;
        }

        Console.Write("Cuantas horas quieres entrenar resistencia? Maximo " + maxHoras + ": ");
        int opcion = Convert.ToInt32(Console.ReadLine());
        if (opcion > maxHoras) opcion = maxHoras;

        for (int i = 0; i < opcion; i++)
        {
            resistencia += 4;
            energia -= 2;
        }
        experiencia += 4;
        Console.WriteLine("Tu guerrero corrio como si hubiera oferta en la tienda de la esquina");
    }

    static void Pelear()
    {
        int costoEnergia = 5;
        if (energia < costoEnergia)
        {
            Console.WriteLine("No puedes pelear, estas mas cansado que un lunes sin cafe");
            return;
        }

        energia -= costoEnergia;
        int fuerzaEnemigo = random.Next(5, 15);
        int resistenciaEnemigo = random.Next(5, 15);
        int poderGuerrero = fuerza + resistencia;
        int poderEnemigo = fuerzaEnemigo + resistenciaEnemigo;

        Console.WriteLine("Peleas contra un vago con poder: " + poderEnemigo);
        if (poderGuerrero > poderEnemigo)
        {
            experiencia += 10;
            Console.WriteLine("Ganaste la pelea, el barrio te respeta");
        }
        else
        {
            experiencia += 3;
            Console.WriteLine("Perdiste la pelea, el vago te robo la cartera");
        }
    }

    static void Dormir()
    {
        Console.WriteLine("El guerrero se acuesta en la banqueta a dormir");
        energia += 10;
        if (energia > 20) energia = 20;
    }

    static void SubirNivel()
    {
        if (experiencia >= nivel * 20)
        {
            nivel++;
            fuerza += 2;
            resistencia += 2;
            experiencia = 0;
            Console.WriteLine("Subiste de nivel, ahora el barrio te tiene miedo");
        }
    }
}
