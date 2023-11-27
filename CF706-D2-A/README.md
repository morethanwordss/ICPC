# Beru-taxi
## Theory
Distance between two points $(x_1, x_2)$ and $(y_1, y_2)$ is

$$ \sqrt {(x_1 - x_2)^2 + (y_1 - y_2)^2} $$ 

## Solution
```c++
#include <bits/stdc++.h>
using namespace std;
 
int32_t main() {
    double a, b; cin >> a >> b;
    int n; cin >> n ;
    double min_time = INT_MAX;
    for (int i = 0; i < n; i ++) {
        double xi, yi, vi; cin >> xi >> yi >> vi;
        double distance = sqrt((xi - a) * (xi - a) + (yi - b) * (yi - b));
        double time = distance / vi;
        min_time = min(min_time, time);
    }
    cout << fixed << setprecision(10) << min_time << "\n";
}
```
