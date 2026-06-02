# Wireframes

> Low-fidelity layouts untuk setiap screen utama.

## Screens Overview

| Screen | Mobile | Status |
|--------|--------|---------|
| Home Feed | ✅ Defined | [View Details](#home-feed-mobile) |
| Request Form | ✅ Defined | [View Details](#request-form-mobile) |
| Order Tracking | ✅ Defined | [View Details](#order-tracking-mobile) |
| Traveler Dashboard | ⬜ Todo | |
| Profile | ⬜ Todo | |

---

## 1. Home Feed (Mobile)
Layar utama untuk menemukan Trip dan Produk.

**Key Elements:**
- Search bar di bagian atas (Sticky).
- Tab Navigation: Explore, Following.
- Traveler Cards (Horizontal Scroll): Menampilkan trip terdekat.
- Product Feed (Vertical): Card berisi foto, harga est, dan profil jastiper.

**Text Wireframe:**
```text
[ Header: Search Bar "Cari barang atau jastiper..." ]
[ Tab: Explore | Following ]

[ Horizontal Scroll: "Jastiper Akan Berangkat" ]
  [ Card: Photo | Nama | Ke: Seoul | Tgl: 15 Jun ]

[ Main Feed (Vertical) ]
  [ Card Item ]
    | [ Traveler Info: @User (Verified) ]
    | [ Image: Product Photo ]
    | [ Title: "Product Name" ]
    | [ Price: Est. IDR X.XXX.XXX ]
    | [ Button: "Lihat Trip" ]
```

---

## 2. Request Form (Mobile)
Tempat shopper mengisi detail barang yang ingin dititip.

**Key Elements:**
- Photo uploader (Max 3).
- Input field untuk spesifikasi (Warna, Ukuran).
- Budget field dengan "Hint" mengenai fee platform.

**Text Wireframe:**
```text
[ Header: "Request Barang" | Back ]

[ Section: Detail Barang ]
  [ Input: "Nama Barang" ]
  [ Upload Area: "Foto Referensi" ]

[ Section: Spesifikasi ]
  [ Input: "Varian/Warna/Ukuran" ]
  [ Textarea: "Catatan Tambahan" ]

[ Button: "Kirim Permintaan" ]
```

---

## 3. Order Tracking (Mobile)
Layar untuk memantau status pesanan dan keamanan dana.

**Key Elements:**
- Stepper progress bar (Requested -> Paid -> Purchased -> Shipped).
- Escrow Status Indicator (e.g., "Dana Tersimpan Aman").
- Bukti pembelian (Foto struk).

**Text Wireframe:**
```text
[ Header: Order #12345 | Status: ON TRIP ]

[ Vertical Stepper ]
  (v) Requested
  (v) Paid (Dana di Escrow)
  (*) Purchased (Action: Upload Proof)
  ( ) Shipped

[ Section: Bukti Pembelian ]
  [ Image Placeholder: Receipt ]

[ Footer: Total Pembayaran ]
```

---

## Guidelines

- Use grayscale only for wireframes.
- Focus on layout and hierarchy.
- Include annotations for interactions.
- Mobile-first approach.
