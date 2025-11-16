namespace Giai_Phuong_Trinh_Bac_2

{
    // Lớp giải phương trình bậc 1
    class PhuongTrinhBac1
    {
        protected double a, b;

        public PhuongTrinhBac1(double a, double b)
        {
            this.a = a;
            this.b = b;
        }

        public virtual void GiaiPTB1()
        {
            if (a == 0)
            {
                if (b == 0)
                    Console.WriteLine("Phương trình vô số nghiệm.");
                else
                    Console.WriteLine("Phương trình vô nghiệm.");
            }
            else
            {
                double x = -b / a;
                Console.WriteLine($"Phương trình bậc 1 có nghiệm: x = {x}");
            }
        }
    }

    // Lớp giải phương trình bậc 2, kế thừa từ bậc 1
    class PhuongTrinhBac2 : PhuongTrinhBac1
    {
        private double c;

        public PhuongTrinhBac2(double a, double b, double c) : base(a, b)
        {
            this.c = c;
        }

        public void GiaiPTB2()
        {
            if (a == 0)
            {
                // Trở thành phương trình bậc 1
                Console.WriteLine("Đây là phương trình bậc 1, sử dụng lớp kế thừa:");
                GiaiPTB1();
            }
            else
            {
                double delta = b * b - 4 * a * c;

                if (delta < 0)
                {
                    Console.WriteLine("Phương trình vô nghiệm thực.");
                }
                else if (delta == 0)
                {
                    double x = -b / (2 * a);
                    Console.WriteLine($"Phương trình có nghiệm kép: x1 = x2 = {x}");
                }
                else
                {
                    double x1 = (-b + Math.Sqrt(delta)) / (2 * a);
                    double x2 = (-b - Math.Sqrt(delta)) / (2 * a);
                    Console.WriteLine($"Phương trình có 2 nghiệm phân biệt: x1 = {x1}, x2 = {x2}");
                }
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Console.OutputEncoding = System.Text.Encoding.UTF8; // Hiển thị tiếng Việt có dấu

            Console.WriteLine("Giải phương trình bậc 2: ax^2 + bx + c = 0");
            Console.Write("Nhập a: ");
            double a = double.Parse(Console.ReadLine());
            Console.Write("Nhập b: ");
            double b = double.Parse(Console.ReadLine());
            Console.Write("Nhập c: ");
            double c = double.Parse(Console.ReadLine());

            PhuongTrinhBac2 ptb2 = new PhuongTrinhBac2(a, b, c);
            ptb2.GiaiPTB2();

            Console.WriteLine("Nhấn phím bất kỳ để thoát...");
            Console.ReadKey();
        }
    }
}
