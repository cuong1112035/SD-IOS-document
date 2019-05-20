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
tTạo 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzE3NzU0NzE2LC0xMDI5MDQzNTU2LC02OD
g5MzkxNTEsMTkxNzMyNjg3OSwtMTQ0NDE5NjIxNCwtMjA4ODc0
NjYxMl19
-->