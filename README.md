from prettytable import PrettyTable

class Toko_buku:
    def __init__(self, nama_buku, id_buku, kategori_buku, tahun_buku, penulis_buku, penerbit_buku):
        self.nama = nama_buku
        self.id = id_buku
        self.kategori = kategori_buku
        self.tahun = tahun_buku
        self.penulis = penulis_buku
        self.penerbit = penerbit_buku
    def __str__(self):
        return f"{self.nama},{self.id},{self.kategori},{self.tahun},{self.penulis},{self.penerbit}"

data_buku = []

def create():
    print("Masukkan data buku yang diinginkan")
    nama_buku = input("Nama Buku: ")
    id_buku = int(input("ID Buku: "))
    kategori_buku = input("Kategori Buku: ")
    tahun_buku = int(input("Tahun Buku: "))
    penulis_buku = input("Penulis Buku: ")
    penerbit_buku = input("Penerbitan Buku: ")
    buku = Toko_buku(nama_buku, id_buku, kategori_buku, tahun_buku, penulis_buku, penerbit_buku)
    data_buku.append(buku)
    print("Buku berhasil ditambahkan!")

def read():
    print("Data buku yang ada:")
    table = PrettyTable(["Nama Buku", "ID Buku", "Kategori", "Tahun", "Penulis", "Penerbit"])
    for buku in data_buku:
        table.add_row([buku.nama, buku.id, buku.kategori, buku.tahun, buku.penulis, buku.penerbit])
    print(table)

def update():
    print("Masukkan ID buku yang ingin diperbarui:")
    id_cari = input("ID Buku: ")
    for buku in data_buku:
        if buku.id == id_cari:
            print(f"Data buku dengan ID {id_cari}:")
            print(buku)
            print("Masukkan data baru:")
            buku.nama = input("Nama Buku: ")
            buku.kategori = input("Kategori Buku: ")
            buku.tahun = int(input("Tahun Buku: "))
            buku.penulis = input("Penulis Buku: ")
            buku.penerbit = input("Penerbit Buku: ")
            print("Data buku berhasil diperbarui!")
        break
    else:
        print(f"Buku dengan ID {id_cari} tidak ditemukan.")

def delete():
    print("Masukkan ID buku yang ingin dihapus:")
    id_hapus = input("ID Buku: ")
    for buku in data_buku:
        if buku.id == id_hapus:
            data_buku.remove(buku)
            print(f"Buku dengan ID {id_hapus} berhasil dihapus.")
        break
    else:
        print(f"Buku dengan ID {id_hapus} tidak ditemukan.")

def main_menu():

    while True:
        print("\nPilih operasi:")
        print("1. Menambahkan Buku")
        print("2. Melihat Stok Buku")
        print("3. Memperbarui Buku")
        print("4. Menghapus Buku")
        print("5. Keluar")

        choice = input("Masukkan pilihan: ")
        if choice == '1':
            create()
        elif choice == '2':
            read()
        elif choice == '3':
            update()
        elif choice == '4':
            delete()
        elif choice == '5':
            print("Terima kasih!")
            break
        else:
            print("Pilihan tidak valid.")

if __name__ == "__main__":
    main_menu()

