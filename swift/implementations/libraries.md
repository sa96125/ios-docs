# Libraries

### Realm

레은 OOP와 Persist objects를 사용할 수 있다. 일반적으로 프로퍼티를 선언한 것과 다르게 @objc dynamic 키워드를 앞에 붙인다. 이는 앱이 실행중일 때 실시간으로 데이터베이스가 우변수를 모니터링 되고 있음을 의미하고 object-c의 기반으로 만들어졌다. App store에서 Realm Browser을 사용하면 .realm 파일을 조작하기 쉽다.



#### 모델 릴레이션

```swift

class Category: Object {
    @objc dynamic var name: String = ""
    @objc dynamic var colour: String = ""
    
    // relationship
    let items = List<Item>()
}

class Item: Object {
    @objc dynamic var title: String = ""
    @objc dynamic var done: Bool = false
    @objc dynamic var dateCreated: Date?
    
    // Relationship
    var parentCategory = LinkingObjects(fromType: Category.self, property: "items")
}


// 공식 문서 추천 강제 선언
let realm = try! Realm()


// 쿼리문 후 받는 자료형은 Results<T>
var todoItems : Results<Item>?

// 각 모델의 자료형이 이미 Realm과 연동되어 있어 
// 모델 그대로 읽기, 쓰기, 삭제가 가능하다.
func loadItems() {

    todoItems = selectedCategory?.items.sorted(byKeyPath: "title", ascending: true)
    
    tableView.reloadData()
}


func save(item: Item) {
    
    do {
        try realm.write {
            realm.add(item)
        }
    } catch {
        print("Error saving context \(error)")
    }

    tableView.reloadData()
}


override func updateModel(at indexPath: IndexPath) {
    if let item = todoItems?[indexPath.row] {
        do {
            try realm.write {
                realm.delete(item)
            }
        } catch {
            print("Error deleting context \(error)")
        }
    }
}

```

### SwipeCellKit



### Chamelon



