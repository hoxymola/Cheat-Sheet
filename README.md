# 입출력

### 입출력 속도 개선

```
cin.tie(0)->sync_with_stdio(0);
```

### 공백 포함해서 한줄 입력

```
string p; getline(cin, p);
```

### 소수점 자리수 조정 (ex. 소수점 아래 6자리)

```
cout << fixed << setprecision(6) << ans << "\n";
```

---

# 비트 연산

### 비트 반전 (~z = -z-1)

```
z ~= z;
```

### n의 k번째 비트

```
n & (1 << k)
n & (1LL << k)
```

### n의 거듭제곱 판별

```
bool isPowerOfTwo(int n) {
    if (!(n & (n - 1))) {
        return true;
    }
    return false;
}
```

### 홀짝 판별 (간지나게)

```
bool isOdd(int n) {
    if (n & 1) {
        return true;
    }
    return false;
}
```

```
bool isEven(int n) {
    if (~n & 1) {
        return true;
    }
    return false;
}
```

### 1의 개수

```
__builtin_popcount(n)
__builtin_popcountll(n)
```

### 처음 1이 등장하기 전 앞의 0의 개수 (count leading zero)

```
__builtin_clz(n)
```

### 처음 1이 등장하기 전 뒤의 0의 개수 (count trailing zero)

```
__builtin_ctz(n)
```

### 패리티 (parity)

```
__builtin_parity(n) // 0 or 1
```

```
int n = 100;  //00000000 00000000 00000000 01100100
cout << __builtin_popcount(n) << "\n";  //3
cout << __builtin_clz(n) << "\n";       //24
cout << __builtin_ctz(n) << "\n";       //2
cout << __builtin_parity(n) << "\n";    //1
```

---

# 이진탐색 (주의: 반환값이 포인터)

### 하한 (x보다 크거나 같은 최소 원소 위치)

```
lower_bound(arr.begin(), arr.end(), x);
```

### 상한 (x보다 큰 최소 원소 위치)

```
upper_bound(arr.begin(), arr.end(), x);
```

---

# 자료구조

### priority queue (min heap)

```
priority_queue<int, vector<int>, greater<int>> pq;
```

### 내림차순 정렬

```
sort(arr.begin(), arr.end(), greater<int>());
```

### 2차원 vector

```
vector<vector<int>> arr(a + 1, vector<int>(b + 1));
```

### 3차원 vector

```
vector<vector<vector<int>>> arr(a + 1, vector<vector<int>>(b + 1, vector<int>(c + 1)));
```

### map (key는 비교 가능한 값, value는 상관 X)

```
map<int, int> m;
```

```
map<string, int> m;
```

```
map<ll, int> m;
```

```
map<vector<int>, int> m;
```

```
//typedef struct {} node;
//bool operator<(node p, node q){} 정의 후에 사용가능
map<node, int> m;
```

### set (비교 가능한 값)

```
set<int> s;
```

```
set<string> s;
```

```
set<ll> s;
```

```
set<vector<int>> s;
```

```
//typedef struct {} node;
//bool operator<(node p, node q){} 정의 후에 사용가능
set<node> s;
```

---

# 수학

### 절댓값

```
abs(x)
```

### 최대공약수

```
//builtin 함수
__gcd(a, b);
```

```
//재귀 함수
int gcd(int a, int b) {
    if (!b) {
        return a;
    }
    return gcd(b, a % b);
}
```

### 최소공배수

```
int lcm(int a, int b) {
    return a * b / __gcd(a, b);
}
```

### 최댓값, 최솟값 (data type 동일해야 됨)

```
//2개
max(a, b)
min(a, b)
```

```
//여러개
max({a, b, c})
min({a, b, c})
```

### 소수 판별

```
bool isPrime(int n) {
    if (n < 2) {
        return false;
    }
    for (int i = 2; i <= sqrt(n); i++) {
        if (!(n % i)) {
            return false;
        }
    }
    return true;
}
```

### 소수 전처리 (prime[x]가 0이면 x는 소수)

```
int Max = 1010101;
vector<int> prime(Max);
prime[0] = prime[1] = 1;
for (int i = 2; i < sqrt(Max); i++) {
	for (int j = i * 2; j < Max; j += i) {
		prime[j] = 1;
	}
}
```

### 조합 전처리

```
int Max 1000;
int COM[Max][Max];
int com(int n, int r) {
    if (COM[n][r]) {
        return COM[n][r];
    }
    if (n == r || r == 0) {
        return 1;
    }
    return COM[n][r] = com(n - 1, r - 1) + com(n - 1, r);
}
```

---

# 라이브러리

### MST (최소 신장 트리)

[문제](https://www.acmicpc.net/problem/1197) / [코드](https://www.acmicpc.net/source/share/95e36661a1c6429886fb11ec6a551609)

### topological sorting (위상 정렬)

[문제](https://www.acmicpc.net/problem/2252) / [코드](https://www.acmicpc.net/source/share/594e74902b6d4e01b5b2654fb0b4b4e2)

### LCA (최소 공통 조상)

[문제](https://www.acmicpc.net/problem/11438) / [코드](https://www.acmicpc.net/source/share/a843fb13f569423b814032e012a74d14)

### segment tree (세그먼트 트리)

[문제](https://www.acmicpc.net/problem/2042) / [코드](https://www.acmicpc.net/source/share/1245da162cc14f6cbfa7f92b6f3174e6)

### bipartite matching (이분 매칭)

[문제](https://www.acmicpc.net/problem/11375) / [코드](https://www.acmicpc.net/source/share/d9a7abbad81e44e895510b6402a14a16)

### KMP (문자열 검색)

[문제](https://www.acmicpc.net/problem/1786) / [코드](https://www.acmicpc.net/source/share/0f6a01130843455097e4c6a86d3cd982)

---

# 템플릿

### 헤더

```
#include <bits/stdc++.h>
```

### 디버그

```
#define debug(x) cout << #x << " is " << x << '\n'
```

### 모든 원소

```
#define all(v) (v).begin(), (v).end()
```

```
sort(all(arr)); //정렬
reverse(all(arr)); //뒤집기
max_element(all(arr)); //최댓값
upper_bound(all(arr), x); //상한
lower_bound(all(arr), x); //하한
fill(all(arr), x); //채우기
```

### 중복 된 원소 제거 (결과값은 정렬 되어있음)

```
#define compress(v) sort(all(v)), (v).erase(unique(all(v)), (v).end())
```

### long long

```
typedef long long ll;
```

### int 최댓값

```
//inf + inf 해도 overflow X
const int inf = 0x3f3f3f3f;
```

### long long 최댓값

```
//lnf + lnf 해도 overflow X
const ll lnf = 0x3f3f3f3f3f3f3f3f;
```

### 모듈러 (문제 조건 확인하고 사용)

```
const int mod = 1e9 + 7;
```

---

# 마음가짐

### 안풀릴 때
- do something instead of nothing and stay organized
- WRITE STUFF DOWN
- DON'T GET STUCK ON ONE APPROACH

### 틀렸을 때

- 배열 크기를 제대로 잡았는가?
- int 범위를 벗어나지는 않는가?
- 정렬되어있다는 조건이 없는데 정렬되어있다고 착각하지 않았는가?
- for문 범위를 제대로 잡았는가?
- N = 0 or 1일 때 제대로 처리했는가?
- 시간이 아슬아슬하다면 최적화를 더 할 수 없는가?

### 안 떠오를 때

- 비슷한 문제를 풀어본 적이 있는가?
- 단순한 방법에서 시작할 수 있을까?
- 내가 문제를 푸는 과정을 수식화할 수 있을까?
- 문제를 단순화할 수 없을까?
- 그림으로 그려볼 수 있을까?
- 수식으로 표현할 수 있을까?
- 그래프로 표현할 수 있을까?
- 문제를 분해할 수 있을까?
- 뒤에서부터 생각해서 문제를 풀 수 있을까?
- 순서를 강제할 수 있을까?
- 특정 형태의 답 만을 고려할 수 있을까?
