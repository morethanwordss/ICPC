# CF593B (Anton and Lines)
## Theory
If two lines $y = k_1 \cdot x + b_1$ and $y = k_2 * x + b_2$ intersects inside a strip $[x_left, x_right]$, 

$$ y_{1_{left}} = k_1 * x_left + b_1 = y1 point on x_left$$
$$ y_{1_right} = k_1 * x_right + b_1 = y1 point on x_right$$
$$ y_{2_left} = k_2 * x_left + b_2 = y2 point on x_left$$
$$ y_{2_right} = k_2 * x_right + b_2 = y2 point on x_right$$

then the order of $(y_{1_left}, y_{2_left)}$ and $(y_{1_right}, y_{2_right})$ will not be the same. To simplify, 

$$ If y_{1_left} < y_{2_left}, then y_{1_right} > y_{2_right} and,$$
$$ If y_{1_left} > y_{2_left}, then y_{1_right} < y_{2_right} and,$$

Now, we pair all ${y_{i_left}, y_{i_right}}$ and sort them according to $y_{i_left}$. Therefore, all $y_{i_left}$ will occur in sorted order. If all $y_{2_right}$ also comes in sorted order then there is no intersection between any two lines. Otherwise, there is.

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
