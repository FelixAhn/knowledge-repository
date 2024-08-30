## 알고리즘이란?
```
 - 문제를 해결하기 위한 일련의 절차를 공식화한 형태로 표현한 것
```

## 좋은 알고리즘을 만들기 위한 조건
```
 - 입력 : 외부에서 제공되는 자료가 0개 이상 존재한다
 - 출력 : 적어도 2개 이상의 서로 다른 결과를 내어야 한다. 즉 모든 입력에 하나의
         출력이 나오면 안된다
 - 명확성 : 수행 과정은 명확하고 모호하지 않은 명령어로 구성되어야 한다
 - 유한성 : 유한 번의 명령어를 수행 후 유한 시간 내에 종료한다
 - 효율성 : 모든 과정은 명백하게 실행 가능한 것이어야 한다
```

## 알고리즘의 종류
### 1. 검색 알고리즘
1-1. 선형 검색(Linear Search) : O(n)
* 배열을 검색하여 원하는 key 값을 찾는 알고리즘
* 배열의 맨 앞부터 순차적으로 훑어가며 검색
```javascript
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i;  // 타겟 값을 찾으면 해당 인덱스를 반환
        }
    }
    return -1;  // 타겟 값을 찾지 못하면 -1을 반환
}

// 예제 배열과 타겟 값
const arr = [5, 3, 8, 4, 2];
const target = 4;

const result = linearSearch(arr, target);

if (result !== -1) {
    console.log(`타겟 값 ${target}은(는) 인덱스 ${result}에 있습니다.`);
} else {
    console.log(`타겟 값 ${target}을(를) 찾을 수 없습니다.`);
}
```
1-2. 이진 검색(Binary Search) : O(logn)
* 정렬된 배열에서 원하는 Key값을 찾는 알고리즘
* 선형검색보다 빠름
```javascript
function binarySearch(arr, target) {
    let left = 0, right = arr.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }

    return -1;
}

const arr = [1, 2, 3, 4, 5];
console.log(binarySearch(arr, 4));  // 출력: 3
```

### 2. 재귀 알고리즘
2-1. 피보나치 수열 : O(2^n)
* 피보나치 수열은 0,1,1,2,3,5,8,13,21,34,55..... 무한대로 이어지는 수열
* 처음 시작하는 두 개의 값은 0과 1로 주어짐
* 다음 값은 앞으 두 개의 값을 더한 값
* 재귀호출구조는 거듭되는 연산이 많아서 복잡 
```javascript
function fibonacci(n) {
    return n <= 1 ? n : fibonacci(n - 1) + fibonacci(n - 2);
}

console.log(fibonacci(6));  // 출력: 8
```
2-2. 최대공약수(GCD) : O(log(n+m))
* 유클리드 알고리즘을 재귀호출 방법으로 사용
* a>=b라면 GCD(a,b) = GCD(b,r)이다. r=a%b
* b가 0이 될 때까지 재귀호출 반복, b가 0이 되면 a가 최대공약수
```javascript
function gcd(a, b) {
    return b === 0 ? a : gcd(b, a % b);
}

console.log(gcd(48, 18));  // 출력: 6
```
2-3 하노이의 탑
* 마찬가지로 재귀호출 방법 사용
* 원반 n-1개를 보조 기둥(aux)으로 옮기고, n번째 원반을 목표 기둥(to)으로 이동시킨 후, 
  다시 n-1개의 원반을 목표 기둥으로 옮김
* hanoi(3, 'A', 'C', 'B')는 세 개의 원반을 A 기둥에서 C 기둥으로 옮기는 순서를 출력
```javascript
function hanoi(n, from, to, aux) {
    if (n === 0) return;
    hanoi(n - 1, from, aux, to);
    console.log(`Move disk ${n} from ${from} to ${to}`);
    hanoi(n - 1, aux, to, from);
}

hanoi(3, 'A', 'C', 'B');
```

### 3. 정렬 알고리즘
3-1. 선택정렬(Selection Sort) : O(n^2)
* 리스트안에 있는 자료들을 (소 -> 대) 순서로 나열
* 가장 단순한 정렬이지만, 많이 비교하므로 복잡도가 높음
* 첫 번쨰 값을 가져올 때 n-1회 비교하여 최솟값을 결과 리스트에 가져옴
* 첫 번쨰 값을 가져올 때 n-2회 비교하여 최솟값을 결과 리스트에 가져옴
* 계속 반복하여 전체 비교횟수는 n(n-1)/2
```javascript
function selectionSort(arr) {
    for (let i = 0; i < arr.length - 1; i++) {
        let minIndex = i;
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIndex]) minIndex = j;
        }
        if (minIndex !== i) {
            [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
        }
    }
    return arr;
}

const arr = [64, 25, 12, 22, 11];
console.log(selectionSort(arr));  // 출력: [11, 12, 22, 25, 64]
```
3-2. 삽입정렬(Insertion Sort) : O(n^2)
* 입력 리스트가 이미 정렬에 가까운 상태라면 복잡도는 O(n)으로 낮아짐
* 일반적으로 선택정렬과 유사한 성능
* 자료가 담긴 리스트에서 순차적으로 값을 가져옴 
* 첫번째값은 그대로 가져오고 두 번째 값을 가져와 결과리스트와 비교 후 위치를 정함
```javascript
function insertionSort(arr) {
    for (let i = 1; i < arr.length; i++) {
        let key = arr[i];
        let j = i - 1;

        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
    return arr;
}

const arr = [5, 2, 9, 1, 5, 6];
console.log(insertionSort(arr));  // 출력: [1, 2, 5, 5, 6, 9]
```
3-3. 병합정렬(Mergy Sort) : O(logn)
* 재귀호출 사용
* 분할정복 방법의 알고리즘
* 자료가 담긴 리스트 가운데 기준으로 2개로 나눈 후 각 리스트에 첫 값을 비교 후
  작은 값을 골라 결과 리스트로 옮기는 방식

```javascript
function mergeSort(arr) {
    if (arr.length <= 1) return arr;

    const mid = Math.floor(arr.length / 2);
    const left = mergeSort(arr.slice(0, mid));
    const right = mergeSort(arr.slice(mid));

    return merge(left, right);
}

function merge(left, right) {
    const result = [];
    let i = 0, j = 0;

    while (i < left.length && j < right.length) {
        if (left[i] < right[j]) {
            result.push(left[i]);
            i++;
        } else {
            result.push(right[j]);
            j++;
        }
    }

    return result.concat(left.slice(i)).concat(right.slice(j));
}

const arr = [38, 27, 43, 3, 9, 82, 10];
console.log(mergeSort(arr));  // 출력: [3, 9, 10, 27, 38, 43, 82]
```
3-4 퀵 정렬(Quick Sort) : O(logn)
* 재귀호출 사용
* 분할정복 방법의 알고리즘
* 병합정렬과는 다르게 특정 값을 피봇으로 정해서 입력리스트를 나눔
* 피봇보다 작은값은 리스트a, 큰값은 리스트b로 저장
* 두 개의 a,b리스트에 재귀호출을 적용해서 정렬된 리스트로 만듬(Like 샌드위치)
```javascript
function quickSort(arr) {
    if (arr.length <= 1) return arr;

    const pivot = arr[arr.length - 1];
    const left = [];
    const right = [];

    for (let i = 0; i < arr.length - 1; i++) {
        if (arr[i] < pivot) left.push(arr[i]);
        else right.push(arr[i]);
    }

    return [...quickSort(left), pivot, ...quickSort(right)];
}

const arr = [3, 6, 8, 10, 1, 2, 1];
console.log(quickSort(arr));  // 출력: [1, 1, 2, 3, 6, 8, 10]
```
3-5 버블 정렬(Bubble Sort) : O(n^2)
* 리스트를 훑어가며 인접한 값 2개씩 비교해서 정렬
* 더 이상 위치 변경이 필요 없을 때까지 반복
* 개인적으로 가장 좋아함
```javascript
function bubbleSort(arr) {
    let n = arr.length;
    let swapped;

    do {
        swapped = false;
        for (let i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
                swapped = true;
            }
        }
        n--;  // 매번 가장 큰 값이 정렬되므로, 비교 범위를 줄입니다.
    } while (swapped);

    return arr;
}

const arr = [5, 1, 4, 2, 8];
console.log(bubbleSort(arr));  // 출력: [1, 2, 4, 5, 8]
```
etc.  이외에도 힙 정렬, 셀 정렬이 있음

| 알고리즘 | 시간 복잡도 (최악) | 시간 복잡도 (평균) | 시간 복잡도 (최선) | 
|--------|----------------|----------------|----------------|
| **선택 정렬** | O(n²)| O(n²) | O(n²) |
| **삽입 정렬** | O(n²) | O(n²) | O(n) |
| **버블 정렬** | O(n²) | O(n²) | O(n) | 
| **병합 정렬** | O(n log n) | O(n log n) | O(n log n) |
| **퀵 정렬**  | O(n²) | O(n log n) | O(n log n) | 

---

## 시간 복잡도(Time Complexity)
```
- 시간 복잡도는 알고리즘이 입력 크기에 따라 실행되는 시간의 증가를 설명하는 개념
- 주로 알고리즘의 효율성을 평가하기 위해 사용되며, 최악의 경우, 평균적인 경우, 최선의 경우에 따라 시
  간 복잡도를 표현 가능
- 일반적으로 알고리즘의 성능을 분석할 때 가장 많이 사용하는 것은 Big-O 표기법
- Big-O 표기법은 입력 크기 n에 대해 알고리즘의 실행 시간이 어떻게 증가하는지를 최악의 경우로 설명
```

## Big-O 표기법
```
- 연산 횟수가 다항식으로 표현된 경우, 최고차항을 제외한 모든 항과 최고차항의 계수를
  제외시킨 후 표기
```

## 시간 복잡도 계산 방법
```javascript
function ex(n){
    let sum = 0;            // 대입연산 1회
    let i = 0;              // 대입연산 1회
    
    for(i = 0; i < n; i++){ // 반복문 초기화 1회, 조건 검사 n+1회, i++연산 n회
        sum += i            // 덧셈 연산 n회
    }
    for(i = 0; i < n; i++){ // 반복문 초기화 1회, 조건 검사 n+1회, i++연산 n회
        sum += i            // 덧셈 연산 n회
    }

    return sum              // 리턴 1회
}
```
* 이 알고리즘의 총 연산횟수는 4n + 7
* Big-O표기 법에따라 O(4n+7) => O(n)


## 시간 복잡도 종류
```
- O(1) : 상수 시간 복잡도
    * 입력 크기에 상관없이 일정한 시간이 소요되는 경우
    * 예시 : 배열의 특정 인덱스에 있는 값 접근, 두 변수 간의 값 교환

- O(log n) : 로그 시간 복잡도
    * 입력 크기가 증가함에 따라 시간이 천천히 증가하는 경우
    * 예시 : 이진 탐색, 균형 이진 트리에서 삽입 또는 검색

- O(n) : 선형 시간 복잡도
    * 입력 크기에 비례하여 시간이 증가하는 경우
    * 예시 : 배열의 모든 요소를 순회하는 경우, 문자열의 길이를 계산하는 경우

- O(nlogn) : 로그 선형 시간 복잡도
    * 입력 크기와 그 로그 값의 곱에 비례하여 시간이 증가하는 경우
    * 예시 : 효율적인 정렬 알고리즘(퀵 정렬, 병합 정렬 등)

- O(n^2) : 이차 시간 복잡도
    * 입력 크기의 제곱에 비례하여 시간이 증가하는 경우
    * 예시 : 이중 반복문을 사용하는 알고리즘(버블 정렬 등)

- O(2^n) : 지수 시간 복잡도
    * 입력 크기가 증가할 때 시간이 지수적으로 증가하는 경우
    * 예시 : 피보나치 수열을 재귀적으로 계산하는 알고리즘, 모든 부분 집합을 생성하는 경우

- O(n!) : 팩토리얼 시간 복잡도
    * 입력 크기 n에 대해 n!에 비례하여 시간이 증가하는 경우
    * 예시 : 외판원 문제(Traveling Salesman Problem)에서 가능한 모든 경로를 탐색하는 경우,
            모든 가능한 순열을 생성하는 경우
```
![시간복잡도 그래프](/img/time%20complexity.png)


## 공간 복잡도(Space Complexity)
```
- 프로그램 실행과 완료에 얼마나 많은 공간(메모리)가 필요한지를 나타냄
- 알고리즘을 실행시키기 위해 필요한 공간은 2가지로 나눔
    * 알고리즘과 무관한 공간(고정 공간)
        - 코드가 저장되는 공간, 알고리즘 실행을 위해 시스템이 필요로 하는 공간
    * 알고리즘과 밀접한 공간(가변 공간)
        - 문제를 해결하기 위해 알고리즘이 필요로 하는 공간, 변수를 저장하는 공
          간, 순환 프로그램일 경우 순환 스택 등
```

## 공간 복잡도 계산 방법
* 상수 공간 복잡도 : O(1)
```javascript
function ex1(n){
    let a = 0;  // 상수 공간
    let b = 1;  // 상수 공간
    return a+b; 
}
```
* 선형 공간 복잡도 : O(n)
```javascript
function ex2(n){
    let arr = new Array(n); // 배열 생성 : O(n)
    for(let i = 0; i < n; i++){
        arr[i] = i;         // 배열 요소 설정 : O(n)
    }
    return array;
}
```
* 이차원 공간 복잡도 : O(n^2)
```javascript
function ex3(n){
    let mat = new Array(n);     // 1차원 배열 생성 : O(n)
    for(let i = 0; i < n; i++){
        mat[i] = new Array(n);  // 2차원 배열 생성 : O(n^2)
    }
    return mat;
}
```
## 시간 복잡도와 공간복잡도의 차이
```
- 시간 복잡도는 얼마나 빠르게 실행되는지 판단
- 공간 복잡도는 얼마나 많은 자원(메모리 공간)이 필요한지를 판단
- 시간 복잡도와 공간 복잡도는 반비례하는 경향이 있음
- 따라서 보통 알고리즘의 성능을 판단할 때는 시간 복잡도 위주로 판단
```
