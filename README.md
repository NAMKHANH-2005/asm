using System;
using System.Collections.Generic;
using System.Linq;
using System.Security.Cryptography;
using System.Text;
using System.Threading.Tasks;

namespace asm3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string name;
            string type;
            int lastmonth;
            int thismonth;

            Console.WriteLine("Enter customer name: ");
            name = Console.ReadLine();
           
            Console.WriteLine("Enter customer type: ");
            type = Console.ReadLine();

            Console.WriteLine("Enter last month's water meter reading: ");
            lastmonth = int.Parse(Console.ReadLine());

            Console.WriteLine("Enter this month's water meter reading: ");
            thismonth = int.Parse(Console.ReadLine());

            Console.WriteLine("The number of people in the household: ");
            int numberofpeople = int.Parse(Console.ReadLine());


            double waterConsumption = thismonth - lastmonth;
            Console.WriteLine("Consume: " + waterConsumption + " M3");

            double consumptionPerPerson = waterConsumption / numberofpeople;
            Console.WriteLine("Consumetion PerPerson: " + consumptionPerPerson + " M3");

            double priceM3;
            double EnviromentFee;
            double VAT;
            double totalPrice;
            double NoVAT;


            if (type == "Household customer")
            {
                if (consumptionPerPerson >= 0 && consumptionPerPerson <= 10)
                {
                    priceM3 = 5.973;
                }
                else if (consumptionPerPerson > 10 && consumptionPerPerson <= 20)
                {
                    priceM3 = 7.052;
                }
                else if (consumptionPerPerson > 20 && consumptionPerPerson <= 30)
                {
                    priceM3 = 8.699;
                }
                else
                {
                    priceM3 = 15.929;
                }
            }
            else if (type == "Administrative agency, public services")
            {
                priceM3 = 9.955;
            }
            else if (type == "Production units")
            {
                priceM3 = 11.615;
            }
            else if (type == "Business services")
            {
                priceM3 = 22.068;
            }
            else
            {
                Console.WriteLine("Invalid customer type!");
                return;
            }
            

            EnviromentFee = consumptionPerPerson * priceM3 * 0.1;
            VAT = consumptionPerPerson * priceM3 * 0.1;
            totalPrice = consumptionPerPerson * priceM3 + EnviromentFee + VAT;
            NoVAT = consumptionPerPerson * priceM3;
            Console.WriteLine($"Total price : " + totalPrice + " VND");

            
            Console.WriteLine("\n----- BILL -----");
            Console.WriteLine("Customer Name: " +name );
            Console.WriteLine("Customer Type: " +type);
            Console.WriteLine("Last Month Reading: " + lastmonth + " M3");
            Console.WriteLine("This Month Reading: " + thismonth + " M3");
            Console.WriteLine("Water Consumption: " + waterConsumption + " M3");
            Console.WriteLine("Price per M3: " + priceM3 + " VND");
            Console.WriteLine("Environment Fee: " + EnviromentFee + " VND");
            Console.WriteLine("VAT: " + VAT + " VND");
            Console.WriteLine("The amount does not include tax: " + NoVAT + " VND");
            Console.WriteLine("Total Price: " + totalPrice + " VND");
            Console.WriteLine("----------------");

            Console.ReadLine();
        }
    }
}
