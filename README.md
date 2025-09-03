BAI1
class HinhChuNhat {
    private double chieuDai;
    private double chieuRong;
    public HinhChuNhat(double chieuDai, double chieuRong) {
        this.chieuDai = chieuDai;
        this.chieuRong = chieuRong;
    }
    public double getChieuDai() {
        return chieuDai;
    }

    public void setChieuDai(double chieuDai) {
        this.chieuDai = chieuDai;
    }

    public double getChieuRong() {
        return chieuRong;
    }

    public void setChieuRong(double chieuRong) {
        this.chieuRong = chieuRong;
    }

  
    public double tinhChuVi() {
        return 2 * (chieuDai + chieuRong);
    }

    
    public double tinhDienTich() {
        return chieuDai * chieuRong;
    }


    public void hienThi() {
        System.out.println("Hình chữ nhật:");
        System.out.println(" - Chiều dài: " + chieuDai);
        System.out.println(" - Chiều rộng: " + chieuRong);
        System.out.println(" - Chu vi: " + tinhChuVi());
        System.out.println(" - Diện tích: " + tinhDienTich());
        System.out.println("--------------------------");
    }
}

public class Main {
    public static void main(String[] args) {
        HinhChuNhat hcn1 = new HinhChuNhat(5, 3);
        HinhChuNhat hcn2 = new HinhChuNhat(10, 4);
        HinhChuNhat hcn3 = new HinhChuNhat(7.5, 2.5);
        hcn1.hienThi();
        hcn2.hienThi();
        hcn3.hienThi();
    }
}




BAI2
class SinhVien {
    private String maSV;
    private String hoTen;
    private int tuoi;
    private static int soLuongSV = 0;

    public SinhVien(String maSV, String hoTen, int tuoi) {
        this.maSV = maSV;
        this.hoTen = hoTen;
        this.tuoi = tuoi;
        soLuongSV++; 
    }
    public String getMaSV() {
        return maSV;
    }

    public void setMaSV(String maSV) {
        this.maSV = maSV;
    }

    public String getHoTen() {
        return hoTen;
    }

    public void setHoTen(String hoTen) {
        this.hoTen = hoTen;
    }

    public int getTuoi() {
        return tuoi;
    }

    public void setTuoi(int tuoi) {
        this.tuoi = tuoi;
    }

    public void hienThi() {
        System.out.println("Mã SV: " + maSV);
        System.out.println("Họ tên: " + hoTen);
        System.out.println("Tuổi: " + tuoi);
        System.out.println("---------------------");
    }

    public static void hienThiTongSV() {
        System.out.println("Tổng số sinh viên đã được tạo: " + soLuongSV);
    }
}

public class Main {
    public static void main(String[] args) {
  
        SinhVien sv1 = new SinhVien("SV001", "Nguyen Van A", 20);
        SinhVien sv2 = new SinhVien("SV002", "Tran Thi B", 21);
        SinhVien sv3 = new SinhVien("SV003", "Le Van C", 19);

        sv1.hienThi();
        sv2.hienThi();
        sv3.hienThi();
        SinhVien.hienThiTongSV();
    }
}





BAI3
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.Scanner;

class TaiKhoan {
    private String soTaiKhoan;
    private String tenChuTaiKhoan;
    private double soDu;

    private static double laiSuatNam = 6.0;

    public TaiKhoan(String soTaiKhoan, String tenChuTaiKhoan, double soDu) {
        this.soTaiKhoan = soTaiKhoan;
        this.tenChuTaiKhoan = tenChuTaiKhoan;
        this.soDu = soDu;
    }

    public void napTien(double soTien) {
        if (soTien > 0) {
            soDu += soTien;
            System.out.println("Nạp " + soTien + " vào tài khoản " + soTaiKhoan + " thành công.");
        } else {
            System.out.println("Số tiền nạp không hợp lệ.");
        }
    }

    public void rutTien(double soTien) {
        if (soTien > 0 && soTien <= soDu) {
            soDu -= soTien;
            System.out.println("Rút " + soTien + " từ tài khoản " + soTaiKhoan + " thành công.");
        } else {
            System.out.println("Rút tiền thất bại (không đủ số dư hoặc số tiền không hợp lệ).");
        }
    }
    public void tinhLaiMotThang() {
        double laiThang = soDu * (laiSuatNam / 100) / 12;
        soDu += laiThang;
        System.out.println("Cộng lãi " + laiThang + " vào tài khoản " + soTaiKhoan);
    }

    public void hienThi() {
        System.out.println("Số TK: " + soTaiKhoan);
        System.out.println("Chủ TK: " + tenChuTaiKhoan);
        System.out.println("Số dư: " + soDu);
        System.out.println("-------------------------");
    }

  
    public String getSoTaiKhoan() {
        return soTaiKhoan;
    }

    public double getSoDu() {
        return soDu;
    }
    public static void thayDoiLaiSuat(double laiSuatMoi) {
        if (laiSuatMoi > 0) {
            laiSuatNam = laiSuatMoi;
            System.out.println("Lãi suất đã thay đổi thành: " + laiSuatNam + "%/năm");
        } else {
            System.out.println("Lãi suất không hợp lệ.");
        }
    }

 
    public static void hienThiLaiSuat() {
        System.out.println("Lãi suất hiện tại: " + laiSuatNam + "%/năm");
    }
}

public class Main {
    public static void main(String[] args) {
        ArrayList<TaiKhoan> danhSach = new ArrayList<>();

        TaiKhoan tk1 = new TaiKhoan("1001", "Nguyen Van A", 5000);
        TaiKhoan tk2 = new TaiKhoan("1002", "Tran Thi B", 8000);
        TaiKhoan tk3 = new TaiKhoan("1003", "Le Van C", 3000);

        danhSach.add(tk1);
        danhSach.add(tk2);
        danhSach.add(tk3);

        System.out.println("== Danh sách tài khoản ban đầu ==");
        for (TaiKhoan tk : danhSach) {
            tk.hienThi();
        }

        tk1.napTien(2000);
        tk2.rutTien(1000);
        tk3.tinhLaiMotThang();


        TaiKhoan.thayDoiLaiSuat(7.5);
        TaiKhoan.hienThiLaiSuat();

        System.out.println("== Danh sách tài khoản sau giao dịch ==");
        for (TaiKhoan tk : danhSach) {
            tk.hienThi();
        }

        String soTKCanTim = "1002";
        System.out.println("== Tìm kiếm tài khoản " + soTKCanTim + " ==");
        for (TaiKhoan tk : danhSach) {
            if (tk.getSoTaiKhoan().equals(soTKCanTim)) {
                tk.hienThi();
            }
        }

        Collections.sort(danhSach, new Comparator<TaiKhoan>() {
            @Override
            public int compare(TaiKhoan t1, TaiKhoan t2) {
                return Double.compare(t2.getSoDu(), t1.getSoDu());
            }
        });

        System.out.println("== Danh sách tài khoản sắp xếp theo số dư giảm dần ==");
        for (TaiKhoan tk : danhSach) {
            tk.hienThi();
        }
    }
}
