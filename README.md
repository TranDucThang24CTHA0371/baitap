using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace De01
{
    class Program
    {
        public string HoTen { get; set; }
        public int NamSinh { get; set; }
        public Person()
        {
            HoTen = "";
            NamSinh = 2000;
        }
        public Person(string hoTen, int namSinh)
        {
            HoTen = hoTen;
            NamSinh = namSinh;
        }
        public virtual void NhapThongTin()
        {
            Console.Write("Ho ten: ");
            HoTen = Console.ReadLine() ?? "";

            Console.Write("Nam Sinh: ");
            NamSinh = int.Parse(Console.ReadLine()!);
        }
        public virtual void XuatThongTin()
        {
            Console.WriteLine($"Ho Ten: {HoTen}");
            Console.WriteLine($"Nam sinh: {NamSinh}");
        }
    }
    class SinhVien : Person
    {
        public string MaSV { get; set; }
        public double DiemTrungBinh { get; set; }
        public SinhVien() : base()
        {
            MaSV = "";
            DiemTrungBinh = 0;
        }
        public SinhVien(string maSV, string hoTen, int namSinh, double diem)
            : base(hoTen, namSinh)
        {
            MaSV = maSV;
            DiemTrungBinh = diem;
        }
        public string XepLoai()
        {
            if (DiemTrungBinh >= 8) return "Gioi";
            if (DiemTrungBinh >= 6.5) return "Kha";
            if (DiemTrungBinh >= 5) return "Trung binh";
            return "Yeu";
        }
        public override void NhapThongTin()
        {
            Console.Write("Ma sinh vien: ");
            MaSV = Console.ReadLine() ?? "";
            base.NhapThongTin();
            Console.Write("Diem trung binh: ");
            DiemTrungBinh =
                double.Parse(Console.ReadLine()!);
        }
        public override void XuatThongTin()
        {
            Console.WriteLine("\n THONG TIN SINH VIEN ");
            Console.WriteLine($"Ma SV: {MaSV}");
            base.XuatThongTin();
            Console.WriteLine($"Diem TB: {DiemTrungBinh}");
            Console.WriteLine($"Xep loai: {XepLoai()}");
        }
    }
    class Program
    {
        static void Main()
        {
            Console.OutputEncoding =
                System.Text.Encoding.UTF8;

            SinhVien sv = new SinhVien();
            sv.NhapThongTin();
            sv.XuatThongTin();

            Console.ReadKey();
        }
    }
}
