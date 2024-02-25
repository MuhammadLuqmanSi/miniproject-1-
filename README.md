from prettytable import PrettyTable

class TokoBuku:
    def __init__(self, nama, id, kategori, tahun, penulis, penerbit):
        self.nama = nama
        self.id = id
        self.kategori = kategori
        self.tahun = tahun
        self.penulis = penulis
        self.penerbit = penerbit

    def __str__(self):
        return f"{self.nama},{self.id},{self.kategori},{self.tahun},{self.penulis},{self.penerbit}"

class Databuku:
    def __init__(self):
        self.data_buku = []

    def create(self):
        print("Masukkan data buku yang diinginkan")
        nama_buku = input("Nama Buku: ")
        id_buku = input("ID Buku: ")
        kategori_buku = input("Kategori Buku: ")
        tahun_buku = input("Tahun Buku: ")
        penulis_buku = input("Penulis Buku: ")
        penerbit_buku = input("Penerbit Buku: ")
        buku = TokoBuku(nama_buku, id_buku, kategori_buku, tahun_buku, penulis_buku, penerbit_buku)
        self.data_buku.append(buku)
        print("Buku berhasil ditambahkan!")

    def read(self):
        print("Data buku yang ada:")
        table = PrettyTable(["Nama Buku", "ID Buku", "Kategori", "Tahun", "Penulis", "Penerbit"])
        for buku in self.data_buku:
            table.add_row([buku.nama, buku.id, buku.kategori, buku.tahun, buku.penulis, buku.penerbit])
        print(table)

    def update(self):
        print("Masukkan ID buku yang ingin diperbarui:")
        id_cari = input("ID Buku: ")
        for buku in self.data_buku:
            if buku.id == id_cari:
                print(f"Data buku dengan ID {id_cari}:")
                print(buku)
                print("Masukkan data baru:")
                buku.nama = input("Nama Buku: ")
                buku.kategori = input("Kategori Buku: ")
                buku.tahun = input("Tahun Buku: ")
                buku.penulis = input("Penulis Buku: ")
                buku.penerbit = input("Penerbit Buku: ")
                print("Data buku berhasil diperbarui!")
                break
        else:
            print(f"Buku dengan ID {id_cari} tidak ditemukan.")

    def delete(self):
        print("Masukkan ID buku yang ingin dihapus:")
        id_hapus = input("ID Buku: ")
        for buku in self.data_buku:
            if buku.id == id_hapus:
                self.data_buku.remove(buku)
                print(f"Buku dengan ID {id_hapus} berhasil dihapus.")
                break
        else:
            print(f"Buku dengan ID {id_hapus} tidak ditemukan.")

    def main_menu(self):
        while True:
            print("===========================================")
            print("|            PROGRAMING STORE             |")
            print("===========================================")
            print("|1. Menambahkan Buku                      |")
            print("|2. Melihat Stok Buku                     |")
            print("|3. Memperbarui Buku                      |")
            print("|4. Menghapus Buku                        |")
            print("|5. Keluar                                |")
            print("===========================================")

            choice = input("Masukkan pilihan: ")
            if choice == '1':
                self.create()
            elif choice == '2':
                self.read()
            elif choice == '3':
                self.update()
            elif choice == '4':
                self.delete()
            elif choice == '5':
                print("Terima kasih!")
                break
            else:
                print("Pilihan tidak valid.")

if __name__ == "__main__":
    toko = Databuku()
    toko.main_menu()
