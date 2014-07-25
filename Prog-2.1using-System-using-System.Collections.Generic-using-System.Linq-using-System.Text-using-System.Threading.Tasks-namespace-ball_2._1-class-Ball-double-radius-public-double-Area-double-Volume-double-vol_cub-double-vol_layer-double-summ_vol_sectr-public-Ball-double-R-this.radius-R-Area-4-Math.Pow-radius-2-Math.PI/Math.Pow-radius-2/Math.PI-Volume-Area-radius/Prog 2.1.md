using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ball_2._1
{
    class Ball
    {
        double radius;
        public double Area;
        double Volume;
        double vol_cub;
        double vol_layer;
        double summ_vol_sectr;

        public Ball(double R)
        {
            this.radius = R;
            Area = 4 * Math.Pow(radius, 2) * Math.PI;// Math.Pow(radius, 2);// *Math.PI;
            Volume = (Area * radius) / 3;
        }
        public void Volume_Cube()
        {
            vol_cub = Math.Pow(radius, 3) * 8;
            Console.WriteLine("Объем куба,в который вписан шар : {0,2}", vol_cub);
        }
        public double Volume_layer(double height_1,double height_2)
        {
            summ_vol_sectr = Math.PI * (Math.Pow(height_1, 2) * (radius - (height_1 / 3)) + Math.Pow(height_2, 2) * (radius - (height_2 / 3)));
            vol_layer = Volume - summ_vol_sectr;
            return (vol_layer);
        }

    }
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Введите радиус шара : ");
            double R = double.Parse(Console.ReadLine());
            Ball ekz = new Ball(R);
            ekz.Volume_Cube();

            Console.Write("Введите высоты шаровых сегментов для расчета шарового слоя.\r\nВысота [1] = ");
            double height_1 = double.Parse(Console.ReadLine());
            Console.Write("Высота [2] = ");
            double height_2 = double.Parse(Console.ReadLine());
            ekz.Volume_layer(height_1, height_2);
            Console.Write("Объем шарового слоя,образованного двумя сегментами : {0:F4}",ekz.Volume_layer(height_1, height_2));
            Console.ReadKey();
        }
    }
}
