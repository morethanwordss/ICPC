# CF593B (Anton and Lines)
## Theory
If two lines $y = k_1 * x + b_1$ and $y = k_2 * x + b_2$ intersects inside a strip $[x_left, x_right]$, 

$$ y_1_left = k_1 * x_left + b_1 = y1 point on x_left$$
$$ y_1_right = k_1 * x_right + b_1 = y1 point on x_right$$
$$ y_2_left = k_2 * x_left + b_2 = y2 point on x_left$$
$$ y_2_right = k_2 * x_right + b_2 = y2 point on x_right$$

then the order of $(y_1_left, y_2_left)$ and $(y_1_right, y_2_right)$ will not be the same. To simplify, 

$$ If y_1_left < y_2_left, then y_1_right > y_2_right and,$$
$$ If y_1_left > y_2_left, then y_1_right < y_2_right and,$$

Now, we pair all ${y_i_left, y_i_right}$ and sort them according to $y_i_left$. Therefore, all $y_i_left$ will occur in sorted order. If all $y_2_right$ also comes in sorted order then there is no intersection between any two lines. Otherwise, there is.

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
