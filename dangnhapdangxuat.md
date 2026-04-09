<img width="737" height="843" alt="image" src="https://github.com/user-attachments/assets/5b64f356-f98f-498f-8f50-f2c2100bce8f" />```mermaid
%%{init: { 'theme': 'base', 'themeVariables': { 'primaryColor': '#ffffff', 'primaryBorderColor': '#000000', 'lineColor': '#000000', 'textColor': '#000000', 'actorBkg': '#ffffff', 'actorBorder': '#000000', 'signalColor': '#000000', 'signalTextColor': '#000000', 'activationBorderColor': '#000000', 'activationBkgColor': '#e0e0e0', 'noteBkgColor': '#ffffff', 'noteBorderColor': '#000000' } } }%%
sequenceDiagram
    actor U as Người dùng
    participant Sys as :Hệ_thống_LMS
    actor Auth as Hệ thống xác thực (Office)

    %% Khung tùy chọn: Quên mật khẩu
    opt Quên mật khẩu
        U->>Sys: chonQuenMatKhau()
        activate Sys
        Sys-->>U: yeuCauCungCapThongTin()
        deactivate Sys
        
        U->>Sys: nhapThongTinKhoiPhuc(email/username)
        activate Sys
        Sys-->>U: thongBaoKetQuaKhoiPhuc()
        deactivate Sys
    end

    %% Khung lựa chọn phương thức đăng nhập
    alt Đăng nhập bằng tài khoản thường
        U->>Sys: nhapThongTin(username, password)
        activate Sys
        Sys-->>U: traVeKetQuaDangNhap()
        deactivate Sys

    else Đăng nhập bằng Office
        U->>Sys: chonDangNhapOffice()
        activate Sys
        Sys->>Auth: yeuCauXacThuc()
        activate Auth
        Auth-->>Sys: traVeKetQuaXacThuc()
        deactivate Auth
        Sys-->>U: traVeKetQuaDangNhap()
        deactivate Sys
    end

    %% Luồng Đăng xuất
    U->>Sys: chonDangXuat()
    activate Sys
    Sys-->>U: xacNhanDangXuat()
    deactivate Sys
```
