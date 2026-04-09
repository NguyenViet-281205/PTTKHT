```mermaid
sequenceDiagram
    actor U as Người dùng
    participant Sys as :Hệ_thống_LMS

    %% Luồng cơ bản: Tìm kiếm và Hiện thị kết quả (Include)
    U->>Sys: nhapTuKhoaTimKiem(tuKhoa)
    activate Sys
    Sys-->>U: hienThiKetQuaTimKiem()
    deactivate Sys

    %% Luồng mở rộng: Lọc kết quả (Extend)
    opt Lọc kết quả
        U->>Sys: chonTieuChiLoc(dieuKienLoc)
        activate Sys
        Sys-->>U: hienThiKetQuaDaLoc()
        deactivate Sys
    end
```
