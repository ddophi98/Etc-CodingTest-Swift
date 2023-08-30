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

## 숫자 다루기
```swift
5 % 2 // 1
5 / 2 // 2
Double(5)/Double(2) // 2.5
```

## Array 다루기
```swift
var lst = [1, 2, 3, 4, 5]
Array(lst.prefix(upTo: 2)) // [1, 2]
Array(lst.suffix(from: 2)) // [3, 4, 5]
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
