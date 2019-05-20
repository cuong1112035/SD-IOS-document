## SDDS Documentation

**UI sẽ xây dựng**: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.20.59.png)

**Bước 1**: 
Tạo 1 class có tên `SDDSBannerImage169` vì `SDDS` cần xây dựng chứa 1 `UIImage` có tỉ lệ là 16:9.  Class `SDDSBannerImage169` có nội dung như sau
```swift
public class SDDSBannerImage169: SDDSComponent {
	@IBOutlet var notiImageView: UIImageView?
}
```
**Lưu ý:** `SDDSBannerImage169` có asset control là `public`  và kế thừa từ `SDDSComponent`

**Bước 2**:
Tạo 1 file `SDDSBannerImage169.xib` chứa 1 `UIImageView` tỉ lệ 16:9 có nội dung như sau: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.20.59.png)

**Bước 3**:
Chỉ ra class owner trong file .xib: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.37.01.png)

**Bước 4**:
Liên kết content file với owner: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2015.47.44.png)

**Bước 5**:
Liên lết `notiImageView` đã tạo ra trong **Bước 1** với file owner: [link](https://github.com/cuong1112035/SD-IOS-document/blob/master/assets/Screen%20Shot%202019-05-20%20at%2016.25.17.png)

**Bước 6**: 
Tạo file `SDDSBannerImage169DataBindable.swift` có nội dung như sau:
```swift
public protocol SDDSBannerImage169Data {
	var notiImageHandler: (() -> UIImage?)? { get }
}

public protocol SDDSBannerImage169Bindable {
	func bind(with data: SDDSBannerImage169Data)
}

protocol SDDSBannerImage169DataBindable: SDDSBannerImage169Bindable where Self: UIView {
	var notiImageView: UIImageView? { get set }
}

extension  SDDSBannerImage169DataBindable {
	public func bind(with data: SDDSBannerImage169Data) {
		DispatchQueue.global(qos: .userInteractive).async { [weak self] in
			guard let image = data.notiImageHandler?() else { return }
			DispatchQueue.main.async {
				self?.notiImageView?.image = image
			}
		}
	}
}
```

 - `notiImageHandler` là logic mà người sử dụng class `SDDSBannerImage169` cần implement vì `UIImage` được cần hiển thị có thể đến từ rất nhiều resource (cache, remote server, local...)
 - `var notiImageView: UIImageView? { get set }` là cái `UIImage` được liên kết vào owner ở **Bước 5**
 - chúng ta cần implement ```func bind(with data: SDDSBannerImage169Data) ```. Đây là function chứa logic để thể hiện cái `UIImage` của user trên UI của chúng ta

**Bước 7**: 
Sử dụng `SDDSBannerImage169DataBindable` cho class `SDDSBannerImage169` như sau

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEyODIzODA1MSw4MDk2MjQ0MjgsMTQyNj
UxOTkxNywxMTIxMDQwNzUwLC0zNjk5NjgyNDksMTI3NDUzMjc4
OCwtNzUwODgyMDI4LDEzMjYwMzQyNzYsLTEwMjkwNDM1NTYsLT
Y4ODkzOTE1MSwxOTE3MzI2ODc5LC0xNDQ0MTk2MjE0LC0yMDg4
NzQ2NjEyXX0=
-->