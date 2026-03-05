import java.util.Locale;
import java.util.Scanner;

public class ATM11 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        scanner.useLocale(Locale.US); // Locale ayarını düzelttim

        // BAKİYELER
        double veyselBakiye = 5000.0;
        String veyselKullaniciAdi = "11156895423";
        String veyselSifre = "1234";

        double kadirBakiye = 3000.0;
        String kadirKullaniciAdi = "74236945712";
        String kadirSifre = "4321";

        System.out.println("ATM'YE HOŞGELDİNİZ");

        // --- DIŞ DÖNGÜ: GİRİŞ EKRANI ---
        while (true) {
            System.out.println("--------------------------------");
            System.out.println("Lütfen 11 haneli TC'nizi GİRİNİZ:");
            String kullaniciadi = scanner.nextLine();

            // --- YENİ EKLENEN KISIM: TC BASAMAK KONTROLÜ ---
            if (kullaniciadi.length() != 11) {
                System.out.println("HATA: TC Kimlik numarası 11 haneli olmalıdır!");
                System.out.println("Ana ekrana dönülüyor...");
                continue; // Döngünün en başına (ATM Hoşgeldiniz kısmına) atar
            }
            // ------------------------------------------------

            System.out.println("Lütfen 4 haneli ŞİFRENİZİ GİRİNİZ:");
            String sifre = scanner.nextLine();

            // --- YENİ EKLENEN KISIM: ŞİFRE BASAMAK KONTROLÜ ---
            if (sifre.length() != 4) {
                System.out.println("HATA: Şifre 4 haneli olmalıdır!");
                System.out.println("Ana ekrana dönülüyor...");
                continue; // Döngünün en başına atar
            }
            // --------------------------------------------------

            // --- VEYSEL GİRİŞİ ---
            if (kullaniciadi.equals(veyselKullaniciAdi) && sifre.equals(veyselSifre)) {
                System.out.println("HOŞGELDİNİZ VEYSEL YILDIZ");
                boolean sistemdeMi = true;

                while (sistemdeMi) {
                    System.out.println("\nİŞLEMİNİZİ SEÇİNİZ:");
                    System.out.println("1- Para Yatır\n2- Para Çek\n3- Bakiye Sorgula\n4- ÇIKIŞ YAP (Ana Menü)");
                    String islem = scanner.nextLine();

                    switch (islem) {
                        case "1":
                            System.out.println("Yatırılacak tutar:");
                            double tutar = scanner.nextDouble();
                            scanner.nextLine(); 
                            veyselBakiye += tutar;
                            System.out.println("Yeni Bakiye: " + veyselBakiye);
                            break;
                        case "2":
                            System.out.println("Çekilecek tutar:");
                            double cekilen = scanner.nextDouble();
                            scanner.nextLine(); 
                            if (cekilen > veyselBakiye) {
                                System.out.println("Yetersiz Bakiye!");
                            } else {
                                veyselBakiye -= cekilen;
                                System.out.println("Yeni Bakiye: " + veyselBakiye);
                            }
                            break;
                        case "3":
                            System.out.println("Mevcut Bakiyeniz: " + veyselBakiye);
                            break;
                        case "4":
                            System.out.println("Ana menüye dönülüyor...");
                            sistemdeMi = false; 
                            break;
                        default:
                            System.out.println("Geçersiz işlem!");
                    }
                    
                    // İşlem sonrası bekleme (Opsiyonel temizlik)
                    if(sistemdeMi) {
                        System.out.println("Devam etmek için Enter'a basınız...");
                        scanner.nextLine();
                    }
                } 

            // --- KADİR GİRİŞİ ---
            } else if (kullaniciadi.equals(kadirKullaniciAdi) && sifre.equals(kadirSifre)) {
                System.out.println("HOŞGELDİNİZ KADİR YILDIZ");
                boolean sistemdeMi = true;

                while (sistemdeMi) {
                    System.out.println("\nİŞLEMİNİZİ SEÇİNİZ:");
                    System.out.println("1- Para Yatır\n2- Para Çek\n3- Bakiye Sorgula\n4- ÇIKIŞ YAP (Ana Menü)");
                    String islem = scanner.nextLine();

                    switch (islem) {
                        case "1":
                            System.out.println("Yatırılacak tutar:");
                            double tutar = scanner.nextDouble();
                            scanner.nextLine();
                            kadirBakiye += tutar;
                            System.out.println("Yeni Bakiye: " + kadirBakiye);
                            break;
                        case "2":
                            System.out.println("Çekilecek tutar:");
                            double cekilen = scanner.nextDouble();
                            scanner.nextLine();
                            if (cekilen > kadirBakiye) {
                                System.out.println("Yetersiz Bakiye!");
                            } else {
                                kadirBakiye -= cekilen;
                                System.out.println("Yeni Bakiye: " + kadirBakiye);
                            }
                            break;
                        case "3":
                            System.out.println("Mevcut Bakiyeniz: " + kadirBakiye);
                            break;
                        case "4":
                            System.out.println("Ana menüye dönülüyor...");
                            sistemdeMi = false;
                            break;
                        default:
                            System.out.println("Geçersiz işlem!");
                    }
                     if(sistemdeMi) {
                        System.out.println("Devam etmek için Enter'a basınız...");
                        scanner.nextLine();
                    }
                }
            } else {
                System.out.println("HATALI KULLANICI ADI VEYA ŞİFRE!");
            }
        } 
    }
}
