---
title: My PS Template
header: header
toc: true
toc_sticky: true
toc_label: "Contents"
excerpt: 내가 쓰는 PS Template
date: 2024-08-23
categories:
    - PS
tags:
  - languages:Korean
  - languages:English
---

출전했던 여러 PS대회에서 reference를 공유하라고 한다.

그래서 지금 내가 쓰는 PS Template를 공유한다.

### C++17

#### Local Compile Option

`make.sh`

```bash
#!/bin/bash

if [ $# -eq 0 ]; then
    echo "no argument!"
else
    g++ -Wall -g -O2 -std=c++17 $1 -o pgm
    ./pgm
fi
```

usage: `sh make.sh (somename).cc`

#### Template

`template.cc`

```cpp
// Reference: calculus0129.github.io/PS/PS_template/

// For Additional Codes
// https://www.acmicpc.net/blog/view/106
// https://www.acmicpc.net/blog/view/114
#include <bits/stdc++.h>
#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>

#define BEGIN(x) x.begin()
#define END(x) x.end()
#define ALL(x) BEGIN(x), END(x)

// #define P 1000000009
// #define SUM(x,y) (x+y)%P

using namespace std;
using namespace __gnu_pbds;

typedef long long ll;

// Define the ordered set using Policy-Based Data Structures
template<typename T>
using ordered_set = tree<T, null_type, less<T>, rb_tree_tag, tree_order_statistics_node_update>;

// Define the ordered set using Policy-Based Data Structures
template<typename T>
using om_set = tree<T, null_type, less_equal<T>, rb_tree_tag, tree_order_statistics_node_update>;

template<typename T>
int m_erase(om_set<T> &om, int val) {
    T idx = om.order_of_key(val);
    om_set<T>::iterator it = om.find_by_order(idx);
    if(*it == val) om.erase(it);
    return val;
}

int main() {
    cin.tie(NULL); ios_base::sync_with_stdio(false); // Speed up IO
    return 0;
}
```

For PST(Persistent Segment Tree), https://www.acmicpc.net/source/80748944


#### FastIO

```cpp
// (Below Code Works! Press control+D for end of input!)
// (e.g. http://boj.kr/6871de4a528d480cb29f6a339f520c33)

//구현 1. fread/fwrite 이용
#pragma GCC optimize("O3")
#pragma GCC target("avx2")
#include <bits/stdc++.h>
#include <unistd.h>
using namespace std;

/////////////////////////////////////////////////////////////////////////////////////////////
/*
 * Author : jinhan814
 * Date : 2021-05-06
 * Source : https://blog.naver.com/jinhan814/222266396476
 * Description : FastIO implementation for cin, cout.
 */
constexpr int SZ = 1 << 20;

class INPUT {
private:
    char read_buf[SZ];
    int read_idx, next_idx;
    bool __END_FLAG__, __GETLINE_FLAG__;
public:
    explicit operator bool() { return !__END_FLAG__; }
    bool IsBlank(char c) { return c == ' ' || c == '\n'; }
    bool IsEnd(char c) { return c == '\0'; }
    char _ReadChar() {
        if (read_idx == next_idx) {
            next_idx = fread(read_buf, sizeof(char), SZ, stdin);
            if (next_idx == 0) return 0;
            read_idx = 0;
        }
        return read_buf[read_idx++];
    }
    char ReadChar() {
        char ret = _ReadChar();
        for (; IsBlank(ret); ret = _ReadChar());
        return ret;
    }
    template<typename T> T ReadInt() {
        T ret = 0; char cur = _ReadChar(); bool flag = 0;
        for (; IsBlank(cur); cur = _ReadChar());
        if (cur == '-') flag = 1, cur = _ReadChar();
        for (; !IsBlank(cur) && !IsEnd(cur); cur = _ReadChar()) ret = 10 * ret + (cur & 15);
        if (IsEnd(cur)) __END_FLAG__ = 1;
        return flag ? -ret : ret;
    }
    string ReadString() {
        string ret; char cur = _ReadChar();
        for (; IsBlank(cur); cur = _ReadChar());
        for (; !IsBlank(cur) && !IsEnd(cur); cur = _ReadChar()) ret.push_back(cur);
        if (IsEnd(cur)) __END_FLAG__ = 1;
        return ret;
    }
    double ReadDouble() {
        string ret = ReadString();
        return stod(ret);
    }
    string getline() {
        string ret; char cur = _ReadChar();
        for (; cur != '\n' && !IsEnd(cur); cur = _ReadChar()) ret.push_back(cur);
        if (__GETLINE_FLAG__) __END_FLAG__ = 1;
        if (IsEnd(cur)) __GETLINE_FLAG__ = 1;
        return ret;
    }
    friend INPUT& getline(INPUT& in, string& s) { s = in.getline(); return in; }
} _in;

class OUTPUT {
private:
    char write_buf[SZ];
    int write_idx;
public:
    ~OUTPUT() { Flush(); }
    explicit operator bool() { return 1; }
    void Flush() {
        fwrite(write_buf, sizeof(char), write_idx, stdout);
        write_idx = 0;
    }
    void WriteChar(char c) {
        if (write_idx == SZ) Flush();
        write_buf[write_idx++] = c;
    }
    template<typename T> int GetSize(T n) {
        int ret = 1;
        for (n = n >= 0 ? n : -n; n >= 10; n /= 10) ret++;
        return ret;
    }
    template<typename T> void WriteInt(T n) {
        int sz = GetSize(n);
        if (write_idx + sz >= SZ) Flush();
        if (n < 0) write_buf[write_idx++] = '-', n = -n;
        for (int i = sz; i-- > 0; n /= 10) write_buf[write_idx + i] = n % 10 | 48;
        write_idx += sz;
    }
    void WriteString(string s) { for (auto& c : s) WriteChar(c); }
    void WriteDouble(double d) { WriteString(to_string(d)); }
} _out;

/* operators */
INPUT& operator>> (INPUT& in, char& i) { i = in.ReadChar(); return in; }
INPUT& operator>> (INPUT& in, string& i) { i = in.ReadString(); return in; }
template<typename T, typename std::enable_if_t<is_arithmetic_v<T>>* = nullptr>
INPUT& operator>> (INPUT& in, T& i) {
    if constexpr (is_floating_point_v<T>) i = in.ReadDouble();
    else if constexpr (is_integral_v<T>) i = in.ReadInt<T>(); return in; }

OUTPUT& operator<< (OUTPUT& out, char i) { out.WriteChar(i); return out; }
OUTPUT& operator<< (OUTPUT& out, string i) { out.WriteString(i); return out; }
template<typename T, typename std::enable_if_t<is_arithmetic_v<T>>* = nullptr>
OUTPUT& operator<< (OUTPUT& out, T i) {
    if constexpr (is_floating_point_v<T>) out.WriteDouble(i);
    else if constexpr (is_integral_v<T>) out.WriteInt<T>(i); return out; }

/* macros */
#define fastio 1
#define cin _in
#define cout _out
#define istream INPUT
#define ostream OUTPUT
/////////////////////////////////////////////////////////////////////////////////////////////
```

### Java

e.g. `b6086_total_flow_edmondskarp.java`

```Java
import java.io.*;
import java.util.*;

public class b6086_total_flow_edmondskarp {
    static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    static BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    static Map<Character, Set<Character>> adj = new HashMap<>();
    static int[][] cap = new int[52][52], flow = new int[52][52];
    static boolean[] labeled = new boolean[52], scanned = new boolean[52];

    private static int charidx(char c) {
        return (int)c<(int)'a'?(int)c-(int)'A':(int)c-(int)'a'+26;
    }
    static Queue<Character> que = new LinkedList<>();
    static Map<Character, Character> prev = new HashMap<>();

    public static void main(String[] args) throws IOException {
        try {
            int n = Integer.parseInt(br.readLine());
            for(int _i=0;_i<n;++_i) {
                String[] input = br.readLine().split(" ");
                char u = input[0].charAt(0), v = input[1].charAt(0);
                int w = Integer.parseInt(input[2]);
                cap[charidx(u)][charidx(v)] = cap[charidx(v)][charidx(u)] = cap[charidx(u)][charidx(v)]+w;
                adj.putIfAbsent(u, new TreeSet<>());
                adj.putIfAbsent(v, new TreeSet<>());
                adj.get(u).add(v);
                adj.get(v).add(u);
            }

            int value=0, v;
            while(labelandscan()) {
                value += augmentflow();
            }
            bw.write(Integer.toString(value));
            bw.close();
        } catch (Exception e) {
            bw.close();
            e.printStackTrace();
        }
    }
    private static boolean labelandscan() throws IOException {
        for(int i=0;i<52;++i) labeled[i] = scanned[i] = false;
        que.clear();
        prev.clear();
        que.add('A');
        labeled[charidx('A')]=true;
        while(!que.isEmpty() && !prev.containsKey('Z')) {
            scan(que.poll());
        }
        return prev.containsKey('Z');
    }
    private static void scan(char node) throws IOException {
//        bw.write("scan: "+node+'\n');
//        bw.flush();
        scanned[charidx(node)] = true;
        for(char v: adj.get(node)) if(cap[charidx(node)][charidx(v)]-flow[charidx(node)][charidx(v)]>0 && !scanned[charidx(v)]) {
            que.add(v);
            prev.put(v, node);
        }
    }
    private static int augmentflow() {
        int f = Integer.MAX_VALUE;
        for(char c = 'Z';c!='A';c=prev.get(c)) {
            f = Math.min(f, cap[charidx(prev.get(c))][charidx(c)]-flow[charidx(prev.get(c))][charidx(c)]);
        }
        for(char c = 'Z';c!='A';c=prev.get(c)) {
            flow[charidx(prev.get(c))][charidx(c)] += f;
            flow[charidx(c)][charidx(prev.get(c))] -= f;
        }
        return f;
    }
}
```

### PyPy3

```python

```

