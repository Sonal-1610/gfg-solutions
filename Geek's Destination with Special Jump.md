## 01. Geek's Destination with Special Jump

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-and-her-destination--145724/1?_gl=1*148j9un*_up*MQ..*_gs*MQ..&gclid=CjwKCAiAq5rYBhB-EiwAhj1RdizxaThHzsk7mXvNT1id9Ul5_J-ZQLM_PXJ1R6xX72BoFu58atzttRoC1TIQAvD_BwE&gbraid=0AAAAAC9yBkDfnr1cXzXxx5LiTpDu73bP-)

### Problem Description

**Task:** Geek starts at position 0 on the positive X-axis and needs to reach or pass position d on the positive X-axis. Geek normally follows a repeating movement pattern:Move forward by a units, taking a seconds.Move backward by b units, taking b seconds.Geek also has a special jump that moves him exactly j units forward in 1 second. He can use it at any time, even in the middle of a forward or backward movement, and the journey ends immediately after the jump.Given five integers a, b, d, l, and r. For every integer j in the range [l, r], find the minimum time required for Geek to reach or pass position d. He may either use the special jump or reach the destination using normal movement alone, whichever takes less time.Return the sum of the minimum times for all jump lengths from l to r. Since, the answer can be large, return modulo 10⁹ + 7. Note: Each jump length is considered independently.Examples:Input: a = 2, b = 1, d = 5, l = 3, r = 4Output: 5Explanation: For j = 3, Geek moves 2 units forward, then takes a jump of 3 units to reach the destination. The minimum time required is 3 seconds.For j = 4, Geek moves 1 unit forward, then takes a jump of 4 units to reach the destination. The minimum time required is 2 seconds.Total sum for the range [l, r] = 3 + 2 = 5.Input: a = 4, b = 2, d = 8, l = 2, r = 4Output: 26Explanation:For j = 2, Geek moves 4 units forward, then 2 units backward. She then moves 4 units forward again and takes a jump of 2 units to reach the destination. The minimum time required is 11 seconds.For j = 3, Geek moves 4 units forward, then 2 units backward. She then moves 3 units forward and takes a jump of 3 units to reach the destination. The minimum time required is 10 seconds.For j = 4, Geek moves 4 units forward, then takes a jump of 4 units to reach the destination. The minimum time required is 5 seconds.Total sum for the range [l, r] = 11 + 10 + 5 = 26.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (C++)

- **Submitted:** 2026-11-25 21:12:49
- **Status:** Correct
- **Marks:** 0

```cpp
class Solution {
    using ll = long long;
    static const ll MOD = 1000000007LL;

    ll prefixSum(ll n, ll c) {
        if (n <= 0) return 0;

        ll q = n / c;
        ll rem = n % c;

        return c * q * (q + 1) / 2 + rem * (q + 1);
    }

public:
    int minTime(int a, int b, int d, int l, int r) {

        ll cnt = r - l + 1;

        ll s1 = cnt * (d + 1LL) - (l + r) * cnt / 2;

        ll c = a - b;

        ll h = min((ll)r, (ll)d - a - 1);

        ll s2 = 0;

        if (h >= l) {
            ll low = d - a - h;
            ll high = d - a - l;

            s2 = prefixSum(high, c) - prefixSum(low - 1, c);
        }

        ll ans = s1 + 2LL * b * s2;

        return ans % MOD;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-11-25 21:12:38
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
    using ll = long long;
    static const ll MOD = 1000000007LL;

    ll prefixSum(ll n, ll c) {
        if (n <= 0) return 0;

        ll q = n / c;
        ll rem = n % c;

        return c * q * (q + 1) / 2 + rem * (q + 1);
    }

public:
    int minTime(int a, int b, int d, int l, int r) {

        ll cnt = r - l + 1;

        ll s1 = cnt * (d + 1LL) - (l + r) * cnt / 2;

        ll c = a - b;

        ll h = min((ll)r, (ll)d - a - 1);

        ll s2 = 0;

        if (h >= l) {
            ll low = d - a - h;
            ll high = d - a - l;

            s2 = prefixSum(high, c) - prefixSum(low - 1, c);
        }

        ll ans = s1 + 2LL * b * s2;

        return ans % MOD;
    }
};
```

*Generated on: 11/25/2026, 9:13:08 PM*