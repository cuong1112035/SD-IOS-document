## SDDS Documentation

**UI sẽ xây dựng**: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.20.59.png)

**Bước 1**: 
Tạo 1 class có tên `SDDSBannerImage169` vì `SDDS` cần xây dựng chứa 1 `UIImage` có tỉ lệ là 16:9
```swift
public class SDDSBannerImage169: SDDSComponent {
	@IBOutlet var notiImageView: UIImageView?
}
```
**Lưu ý:** `SDDSBannerImage169` có asset control là `public`  và kế thừa từ `SDDSComponent`

**Bước 2**:
Tạo 1 file .xib chứa 1 `UIImageView` tỉ lệ 16:9 có nội dung như sau: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.20.59.png)

**Bước 3**:
Chỉ ra class owner trong file .xib: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.37.01.png)

**Bước 4**:
Liên kết content file với owner: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.47.44.png)

**Bước 5**:
Liên lết `notiImageView` trong **B**
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQwMjE1OTk2LC03NTA4ODIwMjgsMTMyNj
AzNDI3NiwtMTAyOTA0MzU1NiwtNjg4OTM5MTUxLDE5MTczMjY4
NzksLTE0NDQxOTYyMTQsLTIwODg3NDY2MTJdfQ==
-->