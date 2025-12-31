flowchart TD
    %% =========================================================
    %% FLOWCHART LENGKAP + MODULAR (BERWARNA) - TO DO LIST C++
    %% =========================================================

    %% =============================
    %% STYLE / WARNA
    %% =============================
    classDef startend fill:#111,stroke:#111,color:#fff;
    classDef core fill:#e8f0fe,stroke:#1a73e8,color:#111;
    classDef login fill:#e6f4ea,stroke:#137333,color:#111;
    classDef reg fill:#fef7e0,stroke:#f9ab00,color:#111;
    classDef todo fill:#fce8e6,stroke:#d93025,color:#111;
    classDef util fill:#f3e8fd,stroke:#9334e6,color:#111;
    classDef decision fill:#fff,stroke:#333,color:#111,stroke-width:2px;
    classDef warn fill:#fff4e5,stroke:#b45309,color:#111;

    %% =========================================================
    %% PROGRAM UTAMA
    %% =========================================================
    A([Start]):::startend --> B[clearScreen()]:::util
    B --> C[judul()]:::util
    C --> D{Loop Menu Login\n(do-while pilih != 0)}:::decision
    D --> E[menuLogin()]:::core
    E --> F[Input pilih (1/2/0)]:::core
    F --> G[clearScreen()]:::util

    G --> H{pilih?}:::decision
    H -->|1 Register| R0
    H -->|2 Login| L0
    H -->|0 Keluar| X0
    H -->|Selain itu| X1[Print "Menu tidak tersedia!"]:::warn

    X1 --> D
    X0[Print "Program selesai. Terima kasih"]:::core --> Z([End]):::startend

    %% =========================================================
    %% REGISTER (MODUL)
    %% =========================================================
    subgraph REG[MODUL REGISTER]
        direction TD
        R0([Mulai Register]):::reg --> R1{jumlahUser == 10?}:::decision
        R1 -->|Ya| R2[Print "User penuh!"]:::warn
        R2 --> REND([Selesai Register]):::reg
        R1 -->|Tidak| R3[Input username[jumlahUser]]:::reg
        R3 --> R4[Input password[jumlahUser]]:::reg
        R4 --> R5[jumlahUser++]:::reg
        R5 --> R6[Print "Register berhasil! Silakan login."]:::reg
        R6 --> R7[pauseProgram()]:::util
        R7 --> R8[clearScreen()]:::util
        R8 --> REND([Selesai Register]):::reg
    end
    REND --> C

    %% =========================================================
    %% LOGIN (MODUL)
    %% =========================================================
    subgraph LOG[MODUL LOGIN]
        direction TD
        L0([Mulai Login]):::login --> L1[Input user]:::login
        L1 --> L2[Input pass]:::login
        L2 --> L3{Loop i=0..jumlahUser-1\nCek username[i]==user && password[i]==pass}:::decision
        L3 -->|Cocok| L4[Print "Login berhasil"]:::login
        L4 --> LOK([Login True]):::login
        L3 -->|Tidak cocok| L5[Print "Login gagal!"]:::warn
        L5 --> LFAIL([Login False]):::login
    end
    LFAIL --> D
    LOK --> TSTART

    %% =========================================================
    %% MENU TODO (SETELAH LOGIN)
    %% =========================================================
    subgraph TODO[MODUL TO-DO LIST (SETELAH LOGIN)]
        direction TD
        TSTART([Masuk Menu To-Do]):::todo --> TLOOP{Loop Menu To-Do\n(do-while menuTodoPilihan != 0)}:::decision

        TLOOP --> TP1[pauseProgram()]:::util
        TP1 --> TP2[clearScreen()]:::util
        TP2 --> TM[menuTodo()]:::todo
        TM --> TI[Input menuTodoPilihan]:::todo
        TI --> TC[clearScreen()]:::util

        TC --> TS{menuTodoPilihan?}:::decision
        TS -->|1| ADD0
        TS -->|2| VIEW0
        TS -->|3| DONE0
        TS -->|4| DEL0
        TS -->|5| VNS0
        TS -->|6| VDS0
        TS -->|7| EDIT0
        TS -->|0| OUT0[Print "Logout berhasil."]:::todo
        TS -->|Selain itu| BAD0[Print "Menu tidak tersedia!"]:::warn

        BAD0 --> TLOOP
        OUT0 --> TEND([Keluar Menu To-Do]):::todo
    end
    TEND --> D

    %% =========================================================
    %% 1. TAMBAH TUGAS (DETAIL + VALIDASI)
    %% =========================================================
    subgraph ADD[1) TAMBAH TUGAS]
        direction TD
        ADD0([Mulai Tambah]):::todo --> A1{jumlahTugas == 10?}:::decision
        A1 -->|Ya| A2[Print "Tugas penuh!"]:::warn
        A2 --> AEND([Selesai Tambah]):::todo

        A1 -->|Tidak| A3[cin.ignore()]:::util
        A3 --> A4[Input nama tugas (getline)]:::todo

        %% KATEGORI
        A4 --> AK0[Label pilih_kategori]:::todo
        AK0 --> AK1[Input pilihKategori (1-3)]:::todo
        AK1 --> AK2{cin.fail()?}:::decision
        AK2 -->|Ya| AK3[cin.clear(); cin.ignore(); Print error]:::warn
        AK3 --> AK0
        AK2 -->|Tidak| AK4{pilihKategori valid 1/2/3?}:::decision
        AK4 -->|1| AK5[kategori="Kuliah"]:::todo
        AK4 -->|2| AK6[kategori="Pekerjaan"]:::todo
        AK4 -->|3| AK7[kategori="Pribadi"]:::todo
        AK4 -->|No| AK8[Print "Kategori tidak valid"]:::warn
        AK8 --> AK0

        %% PRIORITAS
        AK5 --> AP0
        AK6 --> AP0
        AK7 --> AP0

        AP0[Label pilih_prioritas]:::todo --> AP1[Input pilihPrioritas (1-3)]:::todo
        AP1 --> AP2{cin.fail()?}:::decision
        AP2 -->|Ya| AP3[cin.clear(); cin.ignore(); Print error]:::warn
        AP3 --> AP0
        AP2 -->|Tidak| AP4{prioritas valid 1/2/3?}:::decision
        AP4 -->|Ya| AP5[prioritas=pilihPrioritas]:::todo
        AP4 -->|No| AP6[Print "Prioritas tidak valid"]:::warn
        AP6 --> AP0

        AP5 --> A5[status="Belum Selesai"]:::todo
        A5 --> A6[jumlahTugas++]:::todo
        A6 --> A7[Print "Tugas berhasil ditambahkan!"]:::todo
        A7 --> AEND([Selesai Tambah]):::todo
    end
    AEND --> TLOOP

    %% =========================================================
    %% 2. LIHAT SEMUA TUGAS
    %% =========================================================
    subgraph VIEW[2) LIHAT SEMUA TUGAS]
        direction TD
        VIEW0([Mulai Lihat]):::todo --> V1{jumlahTugas==0?}:::decision
        V1 -->|Ya| V2[Print "Belum ada tugas."]:::warn
        V2 --> VEND([Selesai Lihat]):::todo
        V1 -->|Tidak| V3[Loop tampilkan semua tugas\n(nama + status + kategori + prioritas)]:::todo
        V3 --> VEND([Selesai Lihat]):::todo
    end
    VEND --> TLOOP

    %% =========================================================
    %% 3. TANDAI SELESAI
    %% =========================================================
    subgraph DONE[3) TANDAI TUGAS SELESAI]
        direction TD
        DONE0([Mulai Tandai]):::todo --> D1{jumlahTugas==0?}:::decision
        D1 -->|Ya| D2[Print "Belum ada tugas."]:::warn
        D2 --> DEND([Selesai Tandai]):::todo
        D1 -->|Tidak| D3[lihatTugas()]:::todo
        D3 --> D4[Input nomor]:::todo
        D4 --> D5{Nomor valid 1..jumlahTugas?}:::decision
        D5 -->|Tidak| D6[Print "Nomor tidak valid!"]:::warn
        D6 --> DEND([Selesai Tandai]):::todo
        D5 -->|Ya| D7[statusTugas[nomor-1]="Selesai"]:::todo
        D7 --> D8[Print "Tugas ditandai selesai!"]:::todo
        D8 --> DEND([Selesai Tandai]):::todo
    end
    DEND --> TLOOP

    %% =========================================================
    %% 4. HAPUS TUGAS (SHIFT ARRAY)
    %% =========================================================
    subgraph DEL[4) HAPUS TUGAS]
        direction TD
        DEL0([Mulai Hapus]):::todo --> H1{jumlahTugas==0?}:::decision
        H1 -->|Ya| H2[Print "Belum ada tugas."]:::warn
        H2 --> HEND([Selesai Hapus]):::todo
        H1 -->|Tidak| H3[lihatTugas()]:::todo
        H3 --> H4[Input nomor]:::todo
        H4 --> H5{Nomor valid?}:::decision
        H5 -->|Tidak| H6[Print "Nomor tidak valid!"]:::warn
        H6 --> HEND([Selesai Hapus]):::todo
        H5 -->|Ya| H7[Konfirmasi hapus (y/n)]:::todo
        H7 --> H8{Konfirmasi == y/Y?}:::decision
        H8 -->|Tidak| H9[Print "Penghapusan dibatalkan."]:::warn
        H9 --> HEND([Selesai Hapus]):::todo
        H8 -->|Ya| H10[Loop geser array\n(tugas/status/kategori/prioritas)]:::todo
        H10 --> H11[jumlahTugas--]:::todo
        H11 --> H12[Print "Tugas berhasil dihapus!"]:::todo
        H12 --> HEND([Selesai Hapus]):::todo
    end
    HEND --> TLOOP

    %% =========================================================
    %% 5. LIHAT BELUM SELESAI
    %% =========================================================
    subgraph VNS[5) LIHAT TUGAS BELUM SELESAI]
        direction TD
        VNS0([Mulai Lihat Belum Selesai]):::todo --> N1[ada=false]:::todo
        N1 --> N2[Loop: jika status=="Belum Selesai"\n→ tampilkan & ada=true]:::todo
        N2 --> N3{ada==false?}:::decision
        N3 -->|Ya| N4[Print "Tidak ada tugas yang belum selesai."]:::warn
        N4 --> NEND([Selesai]):::todo
        N3 -->|Tidak| NEND([Selesai]):::todo
    end
    NEND --> TLOOP

    %% =========================================================
    %% 6. LIHAT SELESAI
    %% =========================================================
    subgraph VDS[6) LIHAT TUGAS SELESAI]
        direction TD
        VDS0([Mulai Lihat Selesai]):::todo --> S1[ada=false]:::todo
        S1 --> S2[Loop: jika status=="Selesai"\n→ tampilkan & ada=true]:::todo
        S2 --> S3{ada==false?}:::decision
        S3 -->|Ya| S4[Print "Tidak ada tugas yang sudah selesai."]:::warn
        S4 --> SEND([Selesai]):::todo
        S3 -->|Tidak| SEND([Selesai]):::todo
    end
    SEND --> TLOOP

    %% =========================================================
    %% 7. EDIT TUGAS (VALIDASI + OPSIONAL)
    %% =========================================================
    subgraph EDIT[7) EDIT TUGAS]
        direction TD
        EDIT0([Mulai Edit]):::todo --> E1{jumlahTugas==0?}:::decision
        E1 -->|Ya| E2[Print "Belum ada tugas."]:::warn
        E2 --> EEND([Selesai Edit]):::todo

        E1 -->|Tidak| E3[lihatTugas()]:::todo
        E3 --> EN0[Label pilih_nomor]:::todo
        EN0 --> E4[Input nomor]:::todo
        E4 --> E5{cin.fail()?}:::decision
        E5 -->|Ya| E6[cin.clear(); cin.ignore(); Print "Input harus angka!"]:::warn
        E6 --> EN0
        E5 -->|Tidak| E7{nomor valid 1..jumlahTugas?}:::decision
        E7 -->|Tidak| E8[Print "Nomor tidak valid!"]:::warn
        E8 --> EN0

        E7 -->|Ya| E9[index=nomor-1; cin.ignore()]:::util

        %% Nama (opsional)
        E9 --> E10[Input namaBaru (getline)\n(kosong=skip)]:::todo
        E10 --> E11{namaBaru kosong?}:::decision
        E11 -->|Tidak| E12[tugas[index]=namaBaru]:::todo
        E11 -->|Ya| E13[skip]:::todo

        E12 --> E14
        E13 --> E14

        %% Kategori (opsional)
        E14 --> E15[Ubah kategori? (y/n)]:::todo
        E15 --> E16{y/Y?}:::decision
        E16 -->|Tidak| E20
        E16 -->|Ya| EK0[Label pilih_kategori_edit]:::todo
        EK0 --> EK1[Input kategori (1-3)]:::todo
        EK1 --> EK2{cin.fail()?}:::decision
        EK2 -->|Ya| EK3[cin.clear(); cin.ignore(); Print error]:::warn
        EK3 --> EK0
        EK2 -->|Tidak| EK4{1/2/3?}:::decision
        EK4 -->|1| EK5["Kuliah"]:::todo
        EK4 -->|2| EK6["Pekerjaan"]:::todo
        EK4 -->|3| EK7["Pribadi"]:::todo
        EK4 -->|No| EK8[Print "Kategori tidak valid"]:::warn
        EK8 --> EK0
        EK5 --> E20
        EK6 --> E20
        EK7 --> E20

        %% Prioritas (opsional)
        E20 --> E21[Ubah prioritas? (y/n)]:::todo
        E21 --> E22{y/Y?}:::decision
        E22 -->|Tidak| E26
        E22 -->|Ya| EP0[Label pilih_prioritas_edit]:::todo
        EP0 --> EP1[Input prioritas (1-3)]:::todo
        EP1 --> EP2{cin.fail()?}:::decision
        EP2 -->|Ya| EP3[cin.clear(); cin.ignore(); Print error]:::warn
        EP3 --> EP0
        EP2 -->|Tidak| EP4{1/2/3?}:::decision
        EP4 -->|Ya| EP5[prioritas[index]=pilihPrioritas]:::todo
        EP4 -->|No| EP6[Print "Prioritas tidak valid"]:::warn
        EP6 --> EP0
        EP5 --> E26

        %% Selesai
        E26 --> E27[Print "Data tugas berhasil diperbarui!"]:::todo
        E27 --> EEND([Selesai Edit]):::todo
    end
    EEND --> TLOOP
