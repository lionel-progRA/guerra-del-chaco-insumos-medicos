using System;

class Program
{
    static void Main()
    {
        int opcion;
        int pacientes = 0;
        int insumos = 0;
        int consumoDiario = 0;
        bool registrado = false;

        do
        {
            Console.Clear();

            Console.WriteLine("==========================================");
            Console.WriteLine("     SISTEMA DE CONTROL DE INSUMOS");
            Console.WriteLine("          GUERRA DEL CHACO");
            Console.WriteLine("==========================================");

            Console.WriteLine("\n1. Registrar datos");
            Console.WriteLine("2. Evaluar insumos");
            Console.WriteLine("3. Distribuir insumos");
            Console.WriteLine("4. Calcular duración");
            Console.WriteLine("5. Salir");

            Console.Write("\nSeleccione una opción: ");
            opcion = int.Parse(Console.ReadLine());

            Console.Clear();

            switch (opcion)
            {
                case 1:

                    Console.WriteLine("=== REGISTRO DE DATOS ===");

                    // DO WHILE
                    do
                    {
                        Console.Write("Cantidad de pacientes: ");
                        pacientes = int.Parse(Console.ReadLine());

                    } while (pacientes <= 0);


                    do
                    {
                        Console.Write("Cantidad de insumos disponibles: ");
                        insumos = int.Parse(Console.ReadLine());

                    } while (insumos <= 0);


                    do
                    {
                        Console.Write(
                            "Consumo diario de insumos: "
                        );

                        consumoDiario = int.Parse(Console.ReadLine());

                    } while (consumoDiario <= 0);

                    registrado = true;

                    Console.WriteLine(
                        "\nDatos registrados correctamente."
                    );

                    break;


                case 2:

                    if (!registrado)
                    {
                        Console.WriteLine(
                            "Primero debe registrar los datos."
                        );
                    }
                    else
                    {
                        double porPaciente =
                            (double)insumos / pacientes;

                        Console.WriteLine(
                            "=== ESTADO DE LOS INSUMOS ==="
                        );

                        Console.WriteLine(
                            $"Pacientes: {pacientes}"
                        );

                        Console.WriteLine(
                            $"Insumos disponibles: {insumos}"
                        );

                        Console.WriteLine(
                            $"Insumos por paciente: {porPaciente:F2}"
                        );

                        // IF - ELSE IF - ELSE
                        if (porPaciente >= 5)
                        {
                            Console.WriteLine(
                                "\nEstado: SUFICIENTE"
                            );
                        }
                        else if (porPaciente >= 3)
                        {
                            Console.WriteLine(
                                "\nEstado: LIMITADO"
                            );
                        }
                        else
                        {
                            Console.WriteLine(
                                "\nEstado: ESCASO"
                            );
                        }
                    }

                    break;


                case 3:

                    if (!registrado)
                    {
                        Console.WriteLine(
                            "Primero debe registrar los datos."
                        );
                    }
                    else
                    {
                        int cantidad =
                            insumos / pacientes;

                        Console.WriteLine(
                            "=== DISTRIBUCIÓN DE INSUMOS ==="
                        );

                        // FOR
                        for (int i = 1; i <= pacientes; i++)
                        {
                            Console.WriteLine(
                                $"Paciente {i}: {cantidad} insumos"
                            );
                        }
                    }

                    break;


                case 4:

                    if (!registrado)
                    {
                        Console.WriteLine(
                            "Primero debe registrar los datos."
                        );
                    }
                    else
                    {
                        int reserva = insumos;
                        int dias = 0;

                        // WHILE
                        while (reserva >= consumoDiario)
                        {
                            reserva -= consumoDiario;
                            dias++;
                        }

                        Console.WriteLine(
                            "=== DURACIÓN DE LOS INSUMOS ==="
                        );

                        Console.WriteLine(
                            $"Consumo diario: {consumoDiario}"
                        );

                        Console.WriteLine(
                            $"La reserva alcanza para {dias} días."