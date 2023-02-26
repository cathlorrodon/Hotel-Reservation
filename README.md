# Hotel-Reservation

using System;
namespace OnlineHotelReservation
{
    class Program
    {
        static string[,] hotelRooms = new string[10, 5];
        static int totalRooms = hotelRooms.Length;
        static int availableRooms = totalRooms;

        static void Main(string[] args)
        {
            InitializeHotelRooms();

            while (true)
            {
                Console.WriteLine("Welcome to HOTEL DE LUNA!");
                Console.WriteLine("==============================");
                Console.WriteLine("Enter 1 to view available hotel rooms");
                Console.WriteLine("Enter 2 to reserve a room");
                Console.WriteLine("Enter 3 to exit application");
                Console.Write("Enter your choice: ");

                int choice = int.Parse(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        ViewAvailableRooms();
                        break;
                    case 2:
                        ReserveHotelRooms();
                        break;
                    case 3:
                        Console.WriteLine("Thank you for using Online Hotel Reservation System of HOTEL DE LUNA!");
                        return;
                    default:
                        Console.WriteLine("Invalid choice. Please try again.");
                        break;
                }

                Console.WriteLine();
            }
        }

        static void InitializeHotelRooms()
        {
            for (int i = 0; i < hotelRooms.GetLength(0); i++)
            {
                for (int j = 0; j < hotelRooms.GetLength(1); j++)
                {
                    hotelRooms[i, j] = "AVAILABLE";
                }
            }
        }

        static void ViewAvailableRooms()
        {
            Console.WriteLine($"There are {availableRooms} available rooms out of {totalRooms} total rooms.");

            for (int i = 0; i < hotelRooms.GetLength(0); i++)
            {
                for (int j = 0; j < hotelRooms.GetLength(1); j++)
                {
                    Console.Write($"[{hotelRooms[i, j]}] ");
                }

                Console.WriteLine();
            }
        }

        static void ReserveHotelRooms()
        {
            Console.WriteLine("Please enter your name:");
            string name = Console.ReadLine();

            Console.WriteLine("Please enter the floor number (1-10) you want to reserve:");
            int floor = int.Parse(Console.ReadLine());

            Console.WriteLine("Please enter the room number (1-5) you want to reserve:");
            int room = int.Parse(Console.ReadLine());

            if (floor < 0 || floor > 9 || room < 0 || room > 4)
            {
                Console.WriteLine("Invalid floor or room number. Please try again.");
            }
            else if (hotelRooms[floor, room] != "AVAILABLE")
            {
                Console.WriteLine("This hotel room is already reserved. Please choose another one.");
            }
            else
            {
                hotelRooms[floor, room] = name;
                availableRooms--;
                Console.WriteLine($"Floor #[{floor},{room}] number has been reserved for {name}.");
            }
        }
    }
}
