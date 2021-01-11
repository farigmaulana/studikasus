# Studi Kasus

Aplikasi keranjang dimana user dapat menambah atau menghapus item.

# Kegunaan
- User dapat memilih item untuk dimasukkan kedalam keranjang
- User dapat menghapus item pada keranjang
- User dapat memilih voucher untuk pemotongan harga

# Algoritma
  Item-item yg akan dilihat user dimasukkan kedalam listbox sendiri, juga dengan voucher. Setiap event yang di klik pada voucher berisi pemotongan harga secara algoritma. begitu juga dengan item-item makanan dimana setiap item ditambahkan harga akan semakin bertambah, juga saat menghapus item, harga akan mengurang.
        
        private void OnPilihVoucherClicked(object sender, RoutedEventArgs e)
        {
            PilihVoucher pilihVoucherWindow = new PilihVoucher();
            pilihVoucherWindow.SetOnItemSelectedListener(this);
            pilihVoucherWindow.Show();
        }
        
Button voucher yang ditekan akan memunculkan halaman baru. Yaitu daftar voucher.
      
        private void onButtonAddItemClicked(object sender, RoutedEventArgs e)
        {
            Penawaran penawaranWindow = new Penawaran();
            penawaranWindow.SetOnItemSelectedListener(this);
            penawaranWindow.Show();
        }
        
Button tambah yang ditekan akan memunculkan halaman baru. Yaitu daftar item penawaran

        private void listBoxPesanan_ItemClicked(object sender, MouseButtonEventArgs e)
        {
            if (MessageBox.Show("Kamu ingin menghapus item ini?",
                    "Konfirmasi", MessageBoxButton.YesNo) == MessageBoxResult.Yes)
            {
                ListBox listBox = sender as ListBox;
                Item item = listBox.SelectedItem as Item;
                controller.deleteSelectedItem(item);
            }
        }
        
Penghapusan item saat item pada list di tekan dan dikonfirmasi penghapusannya.

        public void onPriceUpdated(double subtotal,  double grantTotal, double potongan)
        {
            labelSubtotal.Content = "Rp " + subtotal;
            labelGrantTotal.Content = "Rp " + grantTotal;
            labelPromoFee.Content = "Rp " + potongan;
        }
        
Semua proses yang terjadi pada harga akan ditampilkan.
