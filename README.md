safe_number
===============

A C/C++ library of uint128 and safe-float(16 digits in decimal) implementation which prioritizes certainty.

This library prioritizes certainty rather than performance and accuracy.

# Usage

```
    auto a1 = safe_number_create(true, 12345, 3); // 12.345
    cout << "a1=" << to_s(a1) << endl;
    test_assert(to_s(a1)=="12.345", "a1 invalid");
    auto a2 = safe_number_create(false, 5432, 2); // -54.32
    cout << "a2=" << to_s(a2) << endl;
    test_assert(to_s(a2)=="-54.32", "a2 invalid");
    auto a3 = safe_number_create("0.123"); // 0.123
    cout << "a3=" << to_s(a3) << endl;
    test_assert(to_s(a3)=="0.123", "a3 invalid");
    auto a4 = safe_number_create(false, 10000, 1); // -1000
    cout << "a4=" << to_s(a4) << endl;
    test_assert(to_s(a4)=="-1000", "a4 invalid");
    auto a5 = safe_number_create("-0"); // 0
    cout << "a5=" << to_s(a5) << endl;
    test_assert(to_s(a5)=="0", "a5 invalid");
    auto a6 = safe_number_create("12345678.987"); // 12345678.987
    cout << "a6=" << to_s(a6) << endl;
    test_assert(to_s(a6)=="12345678.987", "a6 invalid");
    auto a7 = safe_number_create("1.1234567890123"); // 1.12345678
    cout << "a7=" << to_s(a7) << endl;
    test_assert(to_s(a7)=="1.12345678", "a7 invalid");
    auto b1 = safe_number_multiply(a1, a2); // -670.5804
    cout << "b1=" << to_s(b1) << endl;
    test_assert(to_s(b1)=="-670.5804", "b1 invalid");
    auto b2 = safe_number_add(a1, a3); // 12.468
    cout << "b2=" << to_s(b2) << endl;
    test_assert(to_s(b2)=="12.468", "b2 invalid");
    auto b3 = safe_number_div(a1, a5); // NaN
    cout << "b3=" << to_s(b3) << endl;
    test_assert(to_s(b3)=="NaN", "b3 invalid");
    auto b4 = safe_number_div(a6, a2); // 12345678.987 / -54.32 = -227276.85911266
    cout << "b4=" << to_s(b4) << endl;
    test_assert(to_s(b4)=="-227276.85911266", "b4 invalid");
    auto b5 = safe_number_multiply(a6, a6); // 152415789650053.3
    cout << "b5=" << to_s(b5) << endl;
    test_assert(to_s(b5)=="152415789650053.346169", "b5 invalid");
    auto b6 = safe_number_div(safe_number_create("12345678.98765432"), a3); // 12345678.98765432 / 0.123 = 100371373.88336845
    cout << "b6=" << to_s(b6) << endl;
    test_assert(to_s(b6)=="100371373.88336845", "b6 invalid");
    auto b7 = safe_number_mod(safe_number_create("12345678.98765432"), safe_number_create(5)); // 12345678.98765432 % 5 = 3.98765432
    cout << "b7=" << to_s(b7) << endl;
    test_assert(to_s(b7)=="3.98765432", "b7 invalid");
    auto b8 = safe_number_mod(safe_number_create("123"), safe_number_create(5)); // 123 % 5 = 3
    cout << "b8=" << to_s(b8) << endl;
    test_assert(to_s(b8)=="3", "b8 invalid");
    auto a2_int = safe_number_to_int64(a2); // -54
    cout << "int(a2)=" << a2_int << endl;
    test_assert(a2_int==-54, "a2_int invalid");
    test_assert(safe_number_gt(a1, a2), "a1 > a2");
    test_assert(safe_number_gte(a1, a1), "a1 >= a1");
    test_assert(safe_number_eq(a1, safe_number_create("12.345")), "a1 == a1");
    test_assert(safe_number_lt(safe_number_create("1.234"), safe_number_create("1.2340001")), "1.234 < 1.2340001");
    test_assert(safe_number_gt(safe_number_create("-1.234"), safe_number_create("-1.2340001")), "-1.234 > -1.2340001");
    test_assert(safe_number_eq(safe_number_abs(safe_number_create("-123.45")), safe_number_create("123.45")), "abs(-123.45) == 123.45");
    test_assert(std::to_string(a1) == "12.345", "to_string(12.345) == 12.345");

    const SimpleUint128 uint128_0 = simple_uint128_create(0, 0);
    const SimpleUint128 uint128_1 = simple_uint128_create(0, 1);
    auto u1 = simple_uint256_create(simple_uint128_create(1234, 0), simple_uint128_create(0, 123));
    auto u2 = simple_uint256_divmod(u1, simple_uint256_create(uint128_0, simple_uint128_create(0, 12345)));
    cout << "u1=" << std::to_string(u1) << endl;
    test_assert(std::to_string(u1) == "7745943541467164062573364148238260357470306618468618588913787", "u1 invalid");
    cout << "u2.div=" << std::to_string(u2.div_result) << " u2.mod=" << std::to_string(u2.mod_result) << endl;
    test_assert(std::to_string(u2.div_result) == "627455936935371734513840757248947781083054404088182955764", "u2.div invalid");
    test_assert(std::to_string(u2.mod_result) == "7207", "u2.mod invalid");
```
