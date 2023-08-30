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
        for rst in combination(lst: Array(lst.suffix(from: i+1)), remain: remain-1) {
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
        for rst in permutation(lst: Array(lst.prefix(upTo: i) + lst.suffix(from: i+1)), remain: remain-1) {
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
```

## 숫자 다루기
```swift
5 % 2 // 1
5 / 2 // 2
Double(5)/Double(2) // 2.5
Double.infinity // 무한대
pow(4, 2) // 26
sqrt(4) // 2
round(5.123)  // 5.0 (반올림)
ceil(5.123)  // 6.0 (올림)
floor(5.765)  // 5.0 (내림)
trunc(-3.658) // -3.0 (버림)
round(5.123123 * 1000) / 1000 // 5.123 (셋째자리까지 반올림)
String(format: "%.3f", 5.123123) // "5.123" (셋째자리까지 자르기)
```

## Array 다루기
```swift
var lst1 = [1, 2, 3, 4, 5]
var lst2 = ["1", "2", "3", "4", "5"]

Array(lst1.prefix(upTo: 2)) // [1, 2]
Array(lst1.suffix(from: 2)) // [3, 4, 5]

lst2.joined(separator: "-") // 1-2-3-4-5
lst2.joined() // 12345
```

## 문자열 다루기

## Dictionary 다루기

## Set 다루기

## Deque 다루기

## Heap 다루기

## 정규 표현식

## Extension
```swift
// String 인덱스로 접근하기
extension String {
    subscript(_ index: Int) -> Character {
        return self[self.index(self.startIndex, offsetBy: index)]
    }
}
```

## 기타
