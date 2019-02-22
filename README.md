safe_number
===============

A C/C++ library of uint128 and safe-float(16 digits in decimal) implementation which prioritizes certainty.

This library prioritizes certainty rather than performance and accuracy.

# Usage

```
    auto a1 = safe_number_create(true, 12345, 3); // 12.345
    cout << "a1=" << to_s(a1) << endl;
    auto a2 = safe_number_create(false, 5432, 2); // -54.32
    cout << "a2=" << to_s(a2) << endl;
    auto a3 = safe_number_create("0.123"); // 0.123
    cout << "a3=" << to_s(a3) << endl;
    auto a4 = safe_number_create(false, 10000, 1); // -1000
    cout << "a4=" << to_s(a4) << endl;
    auto a5 = safe_number_create("-0"); // 0
    cout << "a5=" << to_s(a5) << endl;
    auto a6 = safe_number_create("12345678.987"); // 12345678.987
    cout << "a6=" << to_s(a6) << endl;
    auto a7 = safe_number_create("1.1234567890123"); // 1.12345678
    cout << "a7=" << to_s(a7) << endl;
    auto b1 = safe_number_multiply(a1, a2); // -670.5804
    cout << "b1=" << to_s(b1) << endl;
    auto b2 = safe_number_add(a1, a3); // 12.468
    cout << "b2=" << to_s(b2) << endl;
    auto b3 = safe_number_div(a1, a5); // NaN
    cout << "b3=" << to_s(b3) << endl;
    auto b4 = safe_number_div(a6, a2); // 12345678.987 / -54.32 = -227276.85911266
    cout << "b4=" << to_s(b4) << endl;
    auto b5 = safe_number_multiply(a6, a6); // 152415789650053.3
    cout << "b5=" << to_s(b5) << endl;
    auto b6 = safe_number_div(safe_number_create("12345678.98765432"), a3); // 12345678.98765432 / 0.123 = 100371373.8833684
    cout << "b6=" << to_s(b6) << endl;
    return 0;
```
