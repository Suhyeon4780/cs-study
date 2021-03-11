# C++_STL

<Br>

## Priority queue

```c++
// #include <queue>
// define 
template<
    class T,
    class Container = std::vector<T>,
    class Compare = std::less<typename Container::value_type>
> class priority_queue;

// example
priority_queue<int> q1;
priority_queue<int, vector<int>, cmp> q2;

// compare overloading, 기본값은 less<T>
struct a{
    int start;
    int end;
    int value;
};

// val의 작은값이 우선순위
struct cmp{
    bool operator()(a t, a t){
        return a.value > b.value;
    }
}
```

---

## Vector

**vector::erase()**

```c++
// define
iterator erase( iterator pos );

// example
v.erase(v.begin()+2); // v[2] 제거
v.erase(v.begin(), v.begin+2) // v[0], v[1], v[2] 제거
```



---

## String

**string::find**

```c++
//define
size_type find( const basic_string& str, size_type pos = 0 );
size_type find( CharT ch, size_type pos = 0 ) const;

//example
string s = "This is an example";
    string::size_type idx;

    idx = s.find("example");
    if(idx == string::npos)
        cout << "Can`t Found";
    else
        cout << idx << endl; // 11

// 4번부터 찾는다
idx = s.find("i", 4);
cout << idx << endl; // 5출력

// 특정 문자를 연속적으로 찾는다
string::size_type begin = 0;
while(1){
        idx = s.find("e", begin);
        if(idx == string::npos){
            cout << "No Found";
            break;
        }
        else
            cout << idx << endl;
        begin = idx+1;
    }
```

**string::erase**

```c++
//define
iterator erase(const_iterator position);

// example
string s = "This is an example";
s.erase(0, 5);
cout << s; // is an example

// 특정 문자를 다 지우고 싶을 때
// 1. remove 사용 include <algorithm>
// remove는 e를 제외한 모든 요소를 앞쪽으로 복사하고 마지막 위치의 iterator를 반환
// erase가 반환된 iterator 부터 end까지 제거
s.erase(remove(s.begin(), s.end(), "e"), s.end());
cout << s; // This an xampl

// 2. find 사용
int idx;
    while(1){
        idx = s.find('e');
        cout << idx << endl;	// 11, 16, -1 출력
        if(idx != -1)
            s.erase(s.begin()+idx);
        else
            break;
    }
cout << s << endl; // This is an xampl
```

**string::replace**

**string::substring**

---

