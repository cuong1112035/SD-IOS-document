## SDDS Documentation 

Chúng ta sẽ sử dụng class `SDDSBannerImage169` đã được xây dựng sẵn để thể hiện 1 cái UIImage của chúng ta lên UI với tỉ lệ 16:9

**Bước 1**:
Tạo 1 view trên UI sử dụng class `SDDSBannerImage169` :  [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2018.51.39.png)

**Bước 2**:
Truyền data vào cho đối tượng của lớp `SDDSBannerImage169`:
```swift
class NotiImageData: SDDSBannerImage169Data {
	var notiImageHandler: (() -> UIImage?)? = { () in
		sleep(3)
		return UIImage(named: "2.1")
	}
}

override func viewDidLoad() {
	super.viewDidLoad()
	notiImage.bind(with: NotiImageData())
}
```
**Lưu ý:** `sleep(3)` dùng để giả sử như UIImage được download từ remote server
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzI0NjU3MzUsNDQ4NTY0MTA1LC03Mj
I1MDU2NjMsLTQxNDI3MTcxMCwtMjA4ODc0NjYxMl19
-->