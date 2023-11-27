# CF593B (Anton and Lines)
## Theory
$$y = k_1 \cdot x + b_1\  .....(i)$$

$$y = k_2 \cdot x + b_2\  .....(ii)$$

Suppose line $(i)$ and $(ii)$ have an intersection point inside a strip $[x_{left}, x_{right}]$.

$$ equation (i) \begin{cases}
y_{1\ left} &\text = k_1 \cdot x_{left} + b_1 \[ $y$ \text {point on} $x_{left}$ \] 
\end{cases}$$

$$ y_{1\ left} = k_1 \cdot x_{left} + b_1 = y_1\ point\ on\ x_{left}$$

$$ y_{1\ right} = k_1 \cdot x_{right} + b_1 = y_1\ point\ on\ x_{right}$$

$$ y_{2\ left} = k_2 \cdot x_{left} + b_2 = y_2\ point\ on\ x_{left}$$

$$ y_{2\ right} = k_2 \cdot x_{left} + b_1 = y_2\ point\ on\ x_{left}$$

If there is an intersection between these two lines, the order of $(y_{11}, y_{21)}$ and $(y_{12}, y_{22})$ will not be the same. To simplify, 

$$If y_{11} < y_{21}, then y_{12} > y_{22} and,$$
$$If y_{11} > y_{21}, then y_{12} < y_{22} and,$$

Now, we pair all ${y_{i1}, y_{i2}}$ and sort them according to $y_{i1}$. Therefore, all $y_{i2}$ will occur in sorted order. If all $y_{22}$ also comes in sorted order then there is no intersection between any two lines. Otherwise, there is.

## Solution
$$ Author : morethanwords $$

```c++
// Time   : O(n log n)
// Memory : O(n)

#include <bits/stdc++.h>
using namespace std;

int32_t main() {

    int n; cin >> n;
    long long x_left, x_right; cin >> x_left >> x_right;
    vector <pair<long long, long long>> pairs;
    for (int i = 0; i < n; i ++) {
        long long k, b; cin >> k >> b;
        long long y_left = k * x_left + b;
        long long y_right = k * x_right + b;
        pairs.push_back({y_left, y_right});
    }
    sort(pairs.begin(), pairs.end());
    for (int i = 1; i < n; i ++) {
        if (pairs[i - 1].second > pairs[i].second) {
            cout << "YES\n";
            return 0;
        }
    }
    cout << "NO\n";

}
```
