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

## 정렬

## 숫자 다루기

## Array 다루기

## 문자열 다루기

## Dictionary 다루기

## Set 다루기

## Deque 다루기

## Heap 다루기

## 정규 표현식

## Extension


## 기타
