# 코딩 테스트 준비 (swift)

## 입력받기
```swift
let input1 = readline()!
let input2 = Int(readLine()!)! 
let input3 = readLine()!.split(separator: " ").map{ Int(String($0))! }
```

## 조합 및 순열
### 조합
```swift
func combination(lst: Array<Int>, remain: Int) -> Array<Array<Int>> {
    if remain == 0 {
        return [[]]
    }
    
    var result = [Array<Int>]()
    for i in 0..<lst.count {
        for rst in combination(lst: Array(lst[i+1..<lst.count]), remain: remain-1) {
            result.append([lst[i]] + rst)
        }
    }
    
    return result
}
```

### 순열
```swift
func permutation(lst: Array<Int>, remain: Int) -> Array<Array<Int>> {
    if remain == 0 {
        return [[]]
    }
    
    var result = [Array<Int>]()
    for i in 0..<lst.count {
        for rst in permutation(lst: Array(lst[0..<i] + lst[i+1..<lst.count]), remain: remain-1) {
            result.append([lst[i]] + rst)
        }
    }
    
    return result
}
```

## 이진법
```swift
let binNum = String(100 ,radix: 2) // 10진수 -> 2진수
let originNum = Int(binNum, radix: 2)! // 2진수 -> 10진수
```

## 정렬
```swift
lst.sort() // 오름차순
lst.sort(by: >) // 내림차순
let newLst = lst.sorted() // 오름차순
let newLst = lst.sorted(by: >) // 내림차순
let newLst = [[1, 2], [3, 4]].sorted {
    ($0[0] < $1[0]) || ($0[1] > $1[1]) // 첫번째는 오름차순, 두번째는 내림차순
}
let newLst = lst.reversed() // 거꾸로
lst.reverse() // 거꾸로
```

## 숫자 다루기
```swift
5 % 2 // 1
5 / 2 // 2
Double(5)/Double(2) // 2.5
Double.infinity // 무한대
pow(4, 2) // 26
sqrt(4) // 2
abs(-2) // 2
round(5.123)  // 5.0 (반올림)
ceil(5.123)  // 6.0 (올림)
floor(5.765)  // 5.0 (내림)
trunc(-3.658) // -3.0 (버림)
round(5.123123 * 1000) / 1000 // 5.123 (셋째자리까지 반올림)
String(format: "%.3f", 5.123123) // "5.123" (셋째자리까지 자르기)
```

## Array 다루기
```swift
// 배열 생성
var lst1 = [1, 2, 3, 4, 5]
var lst2 = ["1", "2", "3", "4", "5"]
var lst3 = Array<Int>()
var lst4 = [Int]()
var lst5 = [Int](repeating: 0, count: 10)

// 요소 개수
lst.count
lst.isEmpty

// 요소 접근
lst[0]
lst[0...2]
lst[0..<2]
lst[...2]
lst[1..<]
lst.first
lst.last

// 요소 추가
lst.append(6)
lst.append(contentsOf: [6, 7, 8])
lst.insert(0, at: 0)
lst.insert(contentsOf: [0, 1], at: 0)

// 요소 변경
lst[0] = 10
lst[0...2] = [6, 7]

// 요소 삭제
lst.remove(at: 2)
lst[0..<2] = []
lst.removeFirst()
lst.removeLast() // 없으면 에러
lst.popLast() // 없으면 nil 반환

// 요소 검색
lst.contains(1)
lst.contains {
    num % 2 == 0
}
lst.first {
    num % 2 == 0
} // 조건 만족하는 첫번째 '값'을 리턴
lst.firstIndex {
    num % 2 == 0
} // 조건 만족하는 첫번째 '인덱스'를 리턴
lst.last {
    num % 2 == 0
} // 조건 만족하는 마지막 '값'을 리턴
lst.lastIndex {
    num % 2 == 0
} // 조건 만족하는 마지막 '인덱스'를 리턴

// 기타
lst.swapAt(0, 4) // 0번째 값과 4번째 값을 스왑
lst.shuffle() // 셔플
lst1 == lst2 // 배열 비교하기
lst2.joined(separator: "-") // 배열은 문자열로 (1-2-3-4-5)
lst2.joined() // 배열을 문자열로 (12345)
```

## 문자열 다루기
```swift
let str = "abcdefg"

// 요소 접근
str[str.startIndex] // a
str[str.index(str.startIndex, offsetBy: 4)] // e
str[str.index(str.endIndex, offsetBy: -1)] // g
str[str.firstIndex(of: "d")]
str[index1...index2]

// 요소 추가
str += "hijk"
str.insert("-", at: index)

// 요소 변경
str.replacingOccurrences(of: "!", with: "?")
str.replaceSubrange(index1..<index2, with: "eee")

// 요소 삭제
str.remove(at: index)
str.removeSubrange(index1..<index2)

// 기타
str.range(of: "bcd")
str.hasPrefix("a")
str.hasSuffix("g")
str.uppercased()
str.lowercased()
```

## Dictionary 다루기
```swift
// 딕셔너리 생성
var dic1 = ["a":1,"b":2]
var dic2 = [String:Int]()
var dic3 = Dictionary<String,Int>()

// 요소 개수
dic.count

// 요소 접근
dic["a"] // 없으면 nil

// 요소 추가 및 변경
dic["d"] = 4

// 요소 삭제
dic["a"] = nil

// 요소 순회
for (key, value) in dic

// 요소 검색
dic.contains(where: condition) // 조건에 부합하는게 있는지 여부
dic.first(where: condition) // 조건에 부합하는 튜플 반환
dic.filter(condition) // 조건에 부합하는 것만 모아서 새 딕셔너리 반환

// 기타
dic.keys
dic.values
```

## Set 다루기

## Deque 다루기

## tuple 다루기

## Heap 다루기

## Extension
```swift
// String 인덱스로 접근하기
extension String {
    subscript(_ index: Int) -> Character {
        return self[self.index(self.startIndex, offsetBy: index)]
    }
}

// SubString 슬라이싱으로 접근하기
extension String {
    subscript(_ range: Range<Int>) -> String {
        let fromIndex = self.index(self.startIndex, offsetBy: range.startIndex)
        let toIndex = self.index(self.startIndex,offsetBy: range.endIndex)
        return String(self[fromIndex..<toIndex])
    }
}
```

## 기타
