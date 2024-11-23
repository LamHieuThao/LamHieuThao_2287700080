using System;
using System.Collections.Generic;
using System.Linq;

namespace QLHocsinh
{
    public class Student
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public int Age { get; set; }
    }

    class Program
    {

        static List<Student> danhSachHocSinh = new List<Student>();

        //a.
       static void ThemHocSinh()
        {
            Console.Write("Nhap ma hoc sinh: ");
            int id = int.Parse(Console.ReadLine());

            Console.Write("Nhap ten hoc sinh: ");
            string name = Console.ReadLine();

            Console.Write("Nhap tuoi hoc sinh: ");
            int age = int.Parse(Console.ReadLine());

            danhSachHocSinh.Add(new Student { Id = id, Name = name, Age = age });
            Console.WriteLine("Đã thêm thành công!");
        }

        
        static void InDanhSach()
        {
            Console.WriteLine("Danh sach tat ca hoc sinh:");
            foreach (var hs in danhSachHocSinh)
            {
                Console.WriteLine($"Id: {hs.Id}, Ten: {hs.Name}, Tuoi: {hs.Age}");
            }
        }

        //b
        static void HocSinhTu15Den18()
        {
            var hocSinhTu15Den18 = danhSachHocSinh.Where(hs => hs.Age >= 15 && hs.Age <= 18);
            Console.WriteLine("Hoc sinh co tuoi tu 15->18:");
            foreach (var hs in hocSinhTu15Den18)
            {
                Console.WriteLine($"Id: {hs.Id}, Ten: {hs.Name}, Tuoi: {hs.Age}");
            }
        }

        //c
        static void HocSinhTenBatDauBangA()
        {
            var hocSinhTenA = danhSachHocSinh.Where(hs => hs.Name.StartsWith("A", StringComparison.OrdinalIgnoreCase));
            Console.WriteLine("Hoc sinh bat dau bang chu 'A':");
            foreach (var hs in hocSinhTenA)
            {
                Console.WriteLine($"Id: {hs.Id}, Ten: {hs.Name}, Tuoi: {hs.Age}");
            }
        }

        //d.
        static void TongTuoi()
        {
            int tongTuoi = danhSachHocSinh.Sum(hs => hs.Age);
            Console.WriteLine($"Tong tuoi cua tat ca hoc sinh: {tongTuoi}");
        }
        //e.

        static void HocSinhTuoiLonNhat()
        {
            var hocSinhTuoiLonNhat = danhSachHocSinh.OrderByDescending(hs => hs.Age).FirstOrDefault();
            if (hocSinhTuoiLonNhat != null)
            {
                Console.WriteLine($"Hoc sinh co tuoi lon nhat: Id: {hocSinhTuoiLonNhat.Id}, Ten: {hocSinhTuoiLonNhat.Name}, Tuoi: {hocSinhTuoiLonNhat.Age}");
            }
            else
            {
                Console.WriteLine("NULL!");
            }
        }

        //f.
        static void SapXepTheoTuoi()
        {
            var danhSachSapXep = danhSachHocSinh.OrderBy(hs => hs.Age);
            Console.WriteLine("Danh sach co tuoi tang dan:");
            foreach (var hs in danhSachSapXep)
            {
                Console.WriteLine($"Id: {hs.Id}, Ten: {hs.Name}, Tuoi: {hs.Age}");
            }
        }

        static void Main(string[] args)
        {
            while (true)
            {
                Console.WriteLine("====== MENU QUAN LY HOC SINH ======");
                Console.WriteLine("1. Them hoc sinh");
                Console.WriteLine("2. Danh sach tat ca hoc sinh: ");
                Console.WriteLine("3. Hoc sinh co 15->18");
                Console.WriteLine("4. Hoc sinh co ten bat dau bang chu 'A'");
                Console.WriteLine("5. Tong tuoi tat ca hoc sinh: ");
                Console.WriteLine("6. Hoc sinh co tuoi lon nhat: ");
                Console.WriteLine("7. Sx danh sach co tuoi tang dan: ");
                Console.WriteLine("0. Thoát");
                Console.Write("Co 8 mon an moi thay chon ak~ (0-7): ");
                string choice = Console.ReadLine();

                switch (choice)
                {
                    case "1":
                        ThemHocSinh();
                        break;
                    case "2":
                        InDanhSach();
                        break;
                    case "3":
                        HocSinhTu15Den18();
                        break;
                    case "4":
                        HocSinhTenBatDauBangA();
                        break;
                    case "5":
                        TongTuoi();
                        break;
                    case "6":
                        HocSinhTuoiLonNhat();
                        break;
                    case "7":
                        SapXepTheoTuoi();
                        break;
                    case "0":
                        Console.WriteLine("Thoat menu!!!.");
                        return;
                    default:
                        Console.WriteLine("Lua chon khong dung. Vui long nhap lai ak !!");
                        break;
                }

                //Console.WriteLine("\nNhấn Enter để tiếp tục...");
                Console.ReadLine();
                Console.Clear();
            }
        }
    }
}
