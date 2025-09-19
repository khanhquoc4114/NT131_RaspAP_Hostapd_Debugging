# RaspAP Debug trên Raspberry Pi 4

## 📌 Giới thiệu

Dự án này tập trung triển khai [RaspAP](https://raspap.com/) trên **Raspberry Pi 4**, biến nó thành một Access Point (AP) không dây, đồng thời phân tích và **debug quá trình kết nối Wi-Fi** (scanning, authentication, association).  

Mục tiêu chính:

- Hiểu cơ chế hoạt động của **hostapd, dnsmasq, lighttpd**.
- Phân tích chi tiết các bước trong kết nối Wi-Fi.  
- Thực hành debug để nhận diện và tối ưu quá trình xử lý kết nối.  

## 🛠️ Công nghệ & Công cụ

- **Raspberry Pi 4**
- **RaspAP** (hostapd, dnsmasq, lighttpd)  
- **SSH (Putty/Terminal)**  
- **GNU Debugger (GDB)**  
- **Wi-Fi debugging tools (Netlink, nl80211, wpa_supplicant)**  

## ⚡ Cài đặt & Cấu hình

### 1. Chuẩn bị

- Raspberry Pi 4  
- Thẻ microSD + Raspberry Pi Imager  
- Dây mạng LAN  

### 2. Cài đặt hệ điều hành

Flash image bằng **Raspberry Pi Imager**, sau đó khởi động Pi.  

### 3. Kết nối tới Raspberry Pi

- **Putty** (Windows) hoặc  
- **SSH qua Terminal**  

### 4. Cài đặt RaspAP

Có 2 cách:  

- **Quick Install** (khuyến nghị)  
- **Manual Install**  

Truy cập `http://raspap.local` để đăng nhập:  

``` bash
Username: admin
Password: secret
```

Tại đây có thể:

- Cấu hình SSID, mật khẩu, bảo mật WPA2/WPA3  
- Quản lý DHCP/DNS  
- Theo dõi client đang kết nối  

## 🔍 Debug quá trình kết nối

### 1. Scanning

- **Active scanning**: client gửi probe request → AP trả lời probe response  
- **Passive scanning**: client lắng nghe beacon từ AP  

### 2. Authentication

- Xác thực client bằng WPA2-PSK  
- Thực hiện quá trình **4-Way Handshake** để sinh khóa bảo mật (PTK, GTK)  

### 3. Association

- Client gửi **association request** → AP trả lời bằng **association response**  
- AP cấp phát địa chỉ IP qua DHCP  

### 4. Công cụ Debug

- Mã nguồn **hostapd**  
- **GDB** để theo dõi tiến trình  
- Phân tích các hàm quan trọng trong hostapd (setup_interface, start_beacon, drv_set_ap, nl80211 event handling, wpa_auth.c)  

## 📊 Kết quả

- Cài đặt thành công RaspAP trên Raspberry Pi 4  
- Debug và phân tích chi tiết các giai đoạn kết nối (probing, authentication, association)  
- Hiểu sâu hơn cách hostapd và wpa_supplicant quản lý quá trình kết nối  

## 📚 Tài liệu tham khảo

- [RaspAP Documentation](https://docs.raspap.com/)  
- [Linux kernel WiFi stack basics](https://wifidiving.substack.com/p/linux-kernel-wifi-stack-basics)  
- [Wi-Fi 4-Way Handshake](https://www.wifi-professionals.com/2019/01/4-way-handshake)  
- [hostapd source code](https://github.com/latelee/hostapd)  
