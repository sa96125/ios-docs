---
description: 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체
---

# Persistent memory store

### NSUserDefaults

데이터베이스로서 사용하면 안된다. pList로서 밑에 예시들 중 하나만 호출한다하더라도 전체리스트를 다 가져온다. 엄청난 양의 데이터를 저장하고 사용한다면 시간적, 성능적 저하 요소가 될 수 있다는 것을 기억하자.

```swift
let defaults = UserDefaults.standard

defaults.set(0.24, forKey: "Volume")
defaults.set(true, forKey: "MusicOn")
defaults.set("Angela", forKey: "PlayerName")
defaults.set(Date(), forKey: "AppLastOpendByUser")
defaults.set([1,2,3], forKey: "myArray")
defaults.set(["name": "Jake"], forKey: "myDictionary")

let voluem = default.float(forKey: "Voluem")
let appLastOpen = defaults.object(forKey: "AppLastOpenedByUser")
let myArray = default.array(forKey: "myArray") as! [Int]
let myDictionary = defaults.object(forKey: "myDictionary")

// 실전 사용
// 저장소 생성
let defaults = UserDefaults.standard

// 데이터를 저장할 때
self.defaults.set(self.itemArray, forKey: "TodoListArray")

// 화면 로드시 불러오기
if let items = (defaults.array(forKey: "TodoListArray") as? [String]) {
    itemArray = items
}
```



### SandBoxing

실행중인 다른 앱에서 데이터의 접근을 막는다. 오직 실행중인 하나의 앱에서만 관리되는 데이터 폴더로 생각할 수 있다. 이 퍼스널 데이터는 랩톱 또는 클라우드 환경에 싱크되어 있기 새로운 장치를 구매하거나 운영체제가 업데이트 되더라도 안전하게 접근하여 사용할 수 있다.

UserDefaults의 경우, 표준 데이터 타입만 취급하여 커스텀 데이터 양식은 저장할 수 없다는 단점이 있다. 하지만 sandBox를 이용하여 해당 데이터 타입을 .plist로 디코드하여 경로에 저장하기 때문에 다채로운 타입 정의 및 저장이 가능하다. 하지만 이또한 마찬가지로 대용량 데이터를 처리하기에 는 한계가 있기에 간단한 데이터를 다룰때만 사용한다.

```swift
let dataFilePath = FileManager
        .default
        .urls(for: .documentDirectory, in: .userDomainMask)
        .first?
        .appendingPathComponent("Items.plist")

// Encoding to plist
func saveitem() {
    let encoder = PropertyListEncoder()
    
    do {
        let data = try encoder.encode(self.itemArray)
        try data.write(to: self.dataFilePath!)
    } catch {
        print("Error encoding item array, \\(error)")
    }

    self.tableView.reloadData()
}

// Decoding to Object
func loadItems() {
    if let data = try? Data(contentsOf: dataFilePath!) {
        let decoder = PropertyListDecoder()
        
        do {
            itemArray = try decoder.decode([TodoItem].self, from: data)
        } catch {
            print(error)
        }
        
    }
}

```



### Keychain

더 안전하고 비밀스러운 정보를 저장할 때 사용할 수 있다. 유저의 개인정보, 비밀번호와 같은 것을 저장이 필요하다면 고려할 수 있다.



### Core Data

이전에는 간단한 싱글 테이블에 적용하였다. 하지만 만약 규모가 커지고 많은 데이터양이 저장되어야할 때, 많은 테이블이 추가되고 연관 관계에 대한 정의가 필요하게 된다. 이때 필요한 것이 Database로 더 복잡한 태스크의 처리할 수 있고 쿼리를 사용해 데이터를 찾는 작업이 쉽게 가능해진다.

IOS 진영에서 가장 일반적인 데이터 베이스 두가지가 Core Data그리고 Realm이다. Core Datas는 오랜시간동안 사랑받아왔고 표준적으로 사용하는 DB이다. 또한 Realm을 더 빠르고 효과적으로 데이터베이스를 처리한다.

기존 프로젝트에서 사용하는 방법은 CodeData 체크 후 생성하는 프로젝트의 Appdelegate에서 필요한 코드를 가져올 수 있다. 기본 적인 용어를 봤을 때 DB에 포함된 Entity는 Class 또는 Table로 매칭할 수 있고 Attribute는 Property와 동일하게 취급한다.

| OOP World | Core Data World | Database World |
| --------- | --------------- | -------------- |
| class     | entity          | table          |
| property  | attribute       | field          |
| Item      | NSManagedObject | row            |

Core Data 프레임 워크에서는 데이터베이스에 직접적으로 접근할 수 없는데 이때 context라는 중간계층을 활용하여 C.R.U.D를 수행할 수 있게 된다.



1\. codeData 체크 후 생성하는 프로젝트의 Appdelegate에서 필요한 코드를 가져온다. \
2\. \[data model inspector] - \[class], codeData파일의 속성을 지정한다.\
\*codegen - \[class Definition]은 컴퓨터 내에 자동으로 swift파일을 만들어 놓고 사용\
\*codegen - \[category Extension]은 내 프로젝트 폴더내에 꼭 만들어 사용해야한다.

```swift
// MARK: - Core Data stack
// NSPersistentContainer는 SQLite 베이스로 시작할 때 호출하는 헬퍼 메서드
lazy var persistentContainer: NSPersistentContainer = {
    
    let container = NSPersistentContainer(name: "DataModel")
    container.loadPersistentStores(completionHandler: { (storeDescription, error) in
        if let error = error as NSError? {
            fatalError("Unresolved error \\(error), \\(error.userInfo)")
        }
    })
    return container
}()

// MARK: - Core Data Saving support
// 데이터를 저장하는 헬퍼 메서드
func saveContext () {
    let context = persistentContainer.viewContext
    if context.hasChanges {
        do {
            try context.save()
        } catch {
            let nserror = error as NSError
            fatalError("Unresolved error \\(nserror), \\(nserror.userInfo)")
        }
    }
}

// AppDelegate의 컨텍스트를 가져온다.
let context = (UIApplication.shared.delegate as! AppDelegate).persistentContainer.viewContext

// 해당 저장소의 클래스를 생성
Item(context: context)

// 저장
func saveitem() {
    do {
        try context.save()
    } catch {
        print("Error saving context \\(error)")
    }

    self.tableView.reloadData()
}

// 읽기
func loadItems() {
    let request : NSFetchRequest<Item> = Item.fetchRequest()
    
    do {
        itemArray = try context.fetch(request)
    } catch {
        print("Error Fetching Data from context \\(error)")
    }
}

// 삭제
func deleteItem() {
		context.delete(itemArray[indexPath.row])
		itemArray.remove(at: indexPath.row)
}
```



### NSPredicate

Foundation Libray, 쿼리문을 작성할 때 사용하는 포맷

```swift
// NSPredicate Cheatcheet
let predicate = NSPredicate(format: "title CONTAINS %@", searchBar.text!)

// 실전
func loadItems(with request: NSFetchRequest<Item> = Item.fetchRequest(), predicate: NSPredicate? = nil) {
        
    let categoryPredicate = NSPredicate(format: "parentCategory.name MATCHES %@", selectedCategory!.name!)
    
    if let addtionalPredicate = predicate {
        request.predicate = NSCompoundPredicate(andPredicateWithSubpredicates: [categoryPredicate, addtionalPredicate])
    } else {
        request.predicate = categoryPredicate
    }
    
    do {
        itemArray = try context.fetch(request)
    } catch {
        print("Error Fetching Data from context \\(error)")
    }
    
    tableView.reloadData()
}
```

