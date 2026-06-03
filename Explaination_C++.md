
---

### 📘 Void Function

| Component | Description |
|-----------|-------------|
| Function type | `void` |
| Return needed? | ❌ No |
| Call in `main()` | `functionName(data, data);` |
| Print in `main()`? | ❌ No (print inside function if needed) |

**Syntax:**
```cpp
void FunctionName (type + data, type + data) {
    // ALLOW any type of data
    // no need write return
}
```

---

### 📘 Int Function

| Component | Description |
|-----------|-------------|
| Function type | `int` |
| Return needed? | ✅ Yes |
| Call in `main()` | `cout << FunctionName(data, data);` |
| Random numbers | `#include <cstdlib>`, `#include <ctime>`, `srand(time(0))` |

**Syntax:**
```cpp
int FunctionName (type + data, type + data) {
    // ONLY can write int under this
    // setting up the something (other than () beside function name) before giving the conditions/rules
    // something = 0 or [] or {};
    // REMEMBER to put return before it ends
    return value;
}
```

---

### 📘 String Function

| Component | Description |
|-----------|-------------|
| Function type | `string` |
| Include | `#include <string>` |
| Return needed? | ✅ Yes |
| Call in `main()` | `cout << FunctionName(data, data);` |

**Syntax:**
```cpp
string FunctionName (type + data, type + data) {
    // write #include <string> for string format input
    // ONLY can write str under this
    // setting up the something (other than () beside function name) before giving the conditions/rules
    // the value = [] or {} or "";
    // REMEMBER to put return before it ends
    return value;
}
```
