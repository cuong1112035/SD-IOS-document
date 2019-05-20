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
Liên lết `notiImageView` trong **Bước 1** với file owner: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2016.25.17.png)


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0ODUzMjUxLDEyNzQ1MzI3ODgsLTc1MD
g4MjAyOCwxMzI2MDM0Mjc2LC0xMDI5MDQzNTU2LC02ODg5Mzkx
NTEsMTkxNzMyNjg3OSwtMTQ0NDE5NjIxNCwtMjA4ODc0NjYxMl
19
-->