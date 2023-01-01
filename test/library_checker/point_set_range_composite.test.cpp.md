---
data:
  _extendedDependsOn:
  - icon: ':heavy_check_mark:'
    path: qitoy/data_structure/segment_tree.hpp
    title: qitoy/data_structure/segment_tree.hpp
  _extendedRequiredBy: []
  _extendedVerifiedWith: []
  _isVerificationFailed: false
  _pathExtension: cpp
  _verificationStatusIcon: ':heavy_check_mark:'
  attributes:
    '*NOT_SPECIAL_COMMENTS*': ''
    PROBLEM: https://judge.yosupo.jp/problem/point_set_range_composite
    links:
    - https://judge.yosupo.jp/problem/point_set_range_composite
  bundledCode: "#line 1 \"test/library_checker/point_set_range_composite.test.cpp\"\
    \n#define PROBLEM \"https://judge.yosupo.jp/problem/point_set_range_composite\"\
    \n#include <bits/stdc++.h>\n#line 3 \"qitoy/data_structure/segment_tree.hpp\"\n\
    \ntemplate<class M>\nclass segment_tree {\n\t\tusing T=typename M::type;\n\n\t\
    public:\n\t\tsegment_tree()=default;\n\t\texplicit segment_tree(int n)\n\t\t\t\
    : _n(n), _vec(2*n, M::e()) { }\n\t\texplicit segment_tree(std::vector<T>& vec)\n\
    \t\t\t: _n(vec.size()), _vec(2*_n) {\n\t\t\t\tfor (int i = 0; i < _n; i++) \n\t\
    \t\t\t\t_vec[_n+i]=vec[i];\n\t\t\t\tfor (int i = _n-1; i > 0; i--)\n\t\t\t\t\t\
    _vec[i]=M::op(_vec[i<<1|0], _vec[i<<1|1]);\n\t\t\t}\n\n\t\tvoid set(int p, T x)\
    \ {\n\t\t\tassert(0<=p and p<_n);\n\t\t\tp+=_n; _vec[p]=x;\n\t\t\twhile(p>1) {\n\
    \t\t\t\tp>>=1;\n\t\t\t\t_vec[p]=M::op(_vec[p<<1|0], _vec[p<<1|1]);\n\t\t\t}\n\t\
    \t}\n\n\t\tvoid add(int p, T x) { set(p, M::op(get(p), x)); }\n\n\t\tT get(int\
    \ p) {\n\t\t\tassert(0<=p and p<_n);\n\t\t\treturn _vec[_n+p];\n\t\t}\n\n\t\t\
    T prod(int l, int r) {\n\t\t\tassert(0<=l and l<=r and r<=_n);\n\t\t\tT ret1=M::e(),\
    \ ret2=M::e();\n\t\t\tl+=_n; r+=_n;\n\t\t\twhile(l<r) {\n\t\t\t\tif(l&1) ret1=M::op(ret1,\
    \ _vec[l++]);\n\t\t\t\tif(r&1) ret2=M::op(_vec[--r], ret2);\n\t\t\t\tl>>=1; r>>=1;\n\
    \t\t\t}\n\t\t\treturn M::op(ret1, ret2);\n\t\t}\n\n\tprivate:\n\t\tint _n;\n\t\
    \tstd::vector<T> _vec;\n};\n#line 4 \"test/library_checker/point_set_range_composite.test.cpp\"\
    \nusing namespace std;\n\nconstexpr int mod=998244353;\n\nclass linear {\n\tusing\
    \ T=pair<int,int>;\n\n\tpublic:\n\tusing type=T;\n\tstatic constexpr T op(T f,\
    \ T g) {\n\t\treturn {(long long)f.first*g.first%mod,\n\t\t   ((long long)f.second*g.first+g.second)%mod};\
    \ // g(f(x))\n\t}\n\tstatic constexpr T e(){return {1,0};}\n};\n\nint main(){\n\
    \n\tcin.tie(nullptr);\n\tios_base::sync_with_stdio(false);\n\n\tint N,Q; cin >>\
    \ N >> Q;\n\tvector<linear::type> V(N);\n\tfor(auto&& [a,b]:V) cin >> a >> b;\n\
    \tsegment_tree<linear> S(V);\n\twhile(Q--) {\n\t\tint q; cin >> q;\n\t\tif(q==0)\
    \ {\n\t\t\tint p,c,d; cin >> p >> c >> d;\n\t\t\tS.set(p, make_pair(c,d));\n\t\
    \t}\n\t\tif(q==1) {\n\t\t\tint l,r,x; cin >> l >> r >> x;\n\t\t\tauto&& [a,b]=S.prod(l,r);\n\
    \t\t\tcout << ((long long)a*x+b)%mod << '\\n';\n\t\t}\n\t}\n\n}\n"
  code: "#define PROBLEM \"https://judge.yosupo.jp/problem/point_set_range_composite\"\
    \n#include <bits/stdc++.h>\n#include \"qitoy/data_structure/segment_tree.hpp\"\
    \nusing namespace std;\n\nconstexpr int mod=998244353;\n\nclass linear {\n\tusing\
    \ T=pair<int,int>;\n\n\tpublic:\n\tusing type=T;\n\tstatic constexpr T op(T f,\
    \ T g) {\n\t\treturn {(long long)f.first*g.first%mod,\n\t\t   ((long long)f.second*g.first+g.second)%mod};\
    \ // g(f(x))\n\t}\n\tstatic constexpr T e(){return {1,0};}\n};\n\nint main(){\n\
    \n\tcin.tie(nullptr);\n\tios_base::sync_with_stdio(false);\n\n\tint N,Q; cin >>\
    \ N >> Q;\n\tvector<linear::type> V(N);\n\tfor(auto&& [a,b]:V) cin >> a >> b;\n\
    \tsegment_tree<linear> S(V);\n\twhile(Q--) {\n\t\tint q; cin >> q;\n\t\tif(q==0)\
    \ {\n\t\t\tint p,c,d; cin >> p >> c >> d;\n\t\t\tS.set(p, make_pair(c,d));\n\t\
    \t}\n\t\tif(q==1) {\n\t\t\tint l,r,x; cin >> l >> r >> x;\n\t\t\tauto&& [a,b]=S.prod(l,r);\n\
    \t\t\tcout << ((long long)a*x+b)%mod << '\\n';\n\t\t}\n\t}\n\n}\n"
  dependsOn:
  - qitoy/data_structure/segment_tree.hpp
  isVerificationFile: true
  path: test/library_checker/point_set_range_composite.test.cpp
  requiredBy: []
  timestamp: '2023-01-01 21:12:37+09:00'
  verificationStatus: TEST_ACCEPTED
  verifiedWith: []
documentation_of: test/library_checker/point_set_range_composite.test.cpp
layout: document
redirect_from:
- /verify/test/library_checker/point_set_range_composite.test.cpp
- /verify/test/library_checker/point_set_range_composite.test.cpp.html
title: test/library_checker/point_set_range_composite.test.cpp
---