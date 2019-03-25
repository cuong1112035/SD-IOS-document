
## SDUITableView, SDCollectionView
Lớp dùng chung cung cấp các tiện ích như: ẩn/hiện empty data view, pull to refresh, prefetching data 2

**Ẩn/hiện empty data view**
 1. Functions và properties liên quan:
	```swift
	func showEmptyDataView()
	func hideEmtyDataView()
	```
 2. Cách sử dụng:
	```swift
	func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
		data.count == 0 ? self.tableView.showEmptyDataView() : self.tableView.hideEmtyDataView()
		return data.count
	}
	```

**Pull to refresh**
 1. Functions và properties liên quan:
	```swift
	var pullToRefreshHandler: (() -> Void)?
	```
 2. Cách sử dụng:
	```swift
	override func viewDidLoad() {
		super.viewDidLoad()
		tableView.pullToRefreshHandler = { [weak self] in
			self?.tableView.reloadData()
		}	
	}
	```
	**Lưu ý:** thêm `[weak self]` vào closure để tránh retain circle
	
**Prefetching data**
 1. Functions và properties liên quan:
	 ```swift
	 func prefetchNextPageIfNeeded(_ fetchNextPageHandler: () -> Void)
	```
2. Mô tả:
	`prefetchNextPageIfNeeded(:)` sẽ quyết định khi nào cần fetch thêm data dựa trên hành động scroll của user trên `UITableView/UICollectionView`. Khi user scroll, lúc đó `fetchNextPageHandler()` sẽ dựa trên các thông số của `UITableView/UICollectionView` (như `contentOffset`, `contentSize`, `frame`...) để yêu cầu load thêm data
3. Cách sử dụng:
	Giả sử chúng ta có 1 function dùng để load data từ sever như sau:
	```swift
	func callAPIThenReloadUIWithNewDataIfNeeded(_ completionHandler: (() -> Void)? = nil) {
		guard isRequestingData == false else { return }
		isRequestingData = true
		NetworkingManager.loadMoreData({ data in
			DispatchQueue.main.async {
				self.data += data
				self.collectionView.reloadData()
				self.isRequestingData = false
				completionHandler?()
			}
		})
	}
	```
	Để sử dụng được chức năng prefetch data này, chúng ta cần gọi hàm `prefetchNextPageIfNeeded(:)` khi user bắt đầu scroll để load thêm data từ sever. Vậy nên chúng ta cần  bắt sự kiện scroll của `UITableView/UICollectionView` bằng cách sử dụng hàm `scrollViewDidScroll(:)` như sau
	```swift
	func scrollViewDidScroll(_ scrollView: UIScrollView) {
		self.collectionView.prefetchNextPageIfNeeded {
			callAPIThenReloadUIWithNewDataIfNeeded()
		}
	}
	```
	Như vậy khi user scroll tới gần cuối của `UITableView/UICollectionView` thì function `callAPIThenReloadUIWithNewDataIfNeeded(:)` sẽ tự động được gọi để load thêm data
	
	**Phụ chú**: (*phụ chú này là optional và giúp đảm bảo luôn có đủ data phục vụ việc scroll của user khi user vừa vào 1 scrollable view controller nào đó*)
	Giả sử chúng ta có hàm `viewDidLoad` như sau:
	```swift
	override func viewDidLoad() {
		super.viewDidLoad()
		callAPIThenReloadUIWithNewDataIfNeeded()
	}
	```
	Giả sử như server trả về 15 records và sau khi render 15 records đó lên UI thì chúng ta có `contentSize` của `UITableView/UICollectionView` là 400 trong khi chiều cao của `UITableView/UICollectionView` chỉ là 350. Điều đó dẫn đến việc user chỉ có thể scroll được 1 đoạn rất ngắn và phải đợi kết quả từ `prefetchNextPageIfNeeded` được trả về để có thêm data để scroll tiếp.
		Để giải quyết vấn đề này thì chúng ta sẽ sửa lại hàm `viewDidLoad()` như sau:
	```swift
	override func viewDidLoad() {
		super.viewDidLoad()
		callAPIThenReloadUIWithNewDataIfNeeded {
			self.tableView.prefetchNextPageIfNeeded {
				self.callAPIThenReloadUIWithNewDataIfNeeded()
			}
		}
	}
	```
	như vậy, hàm `callAPIThenReloadUIWithNewDataIfNeeded(:)` có thể sẽ được gọi đến 2 lần trong `viewDidLoad()` để đảm bảo user có đủ data để scroll
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMwMTI2MDYwOSwtNzUyOTAwODQ1XX0=
-->