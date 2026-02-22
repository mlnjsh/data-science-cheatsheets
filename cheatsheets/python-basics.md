# Python Basics Cheatsheet

## Data Types

| Type | Example | Mutable |
|------|---------|---------|
| `int` | `42` | No |
| `float` | `3.14` | No |
| `str` | `"hello"` | No |
| `bool` | `True` | No |
| `list` | `[1, 2, 3]` | Yes |
| `tuple` | `(1, 2, 3)` | No |
| `dict` | `{"a": 1}` | Yes |
| `set` | `{1, 2, 3}` | Yes |

## List Comprehensions

```python
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]
flat = [x for row in matrix for x in row]
pairs = [(x, y) for x in range(3) for y in range(3)]
```

## Dict Comprehensions

```python
word_lengths = {word: len(word) for word in words}
filtered = {k: v for k, v in d.items() if v > 0}
```

## Lambda Functions

```python
square = lambda x: x ** 2
add = lambda x, y: x + y
sorted_list = sorted(data, key=lambda x: x["score"], reverse=True)
```

## Useful Built-ins

| Function | Usage | Example |
|----------|-------|---------|
| `map()` | Apply function to iterable | `list(map(str, [1,2,3]))` |
| `filter()` | Filter by condition | `list(filter(lambda x: x>0, nums))` |
| `zip()` | Combine iterables | `list(zip(names, scores))` |
| `enumerate()` | Index + value | `for i, v in enumerate(lst)` |
| `any() / all()` | Boolean checks | `any(x > 5 for x in nums)` |

## Decorators

```python
def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"{func.__name__}: {time.time()-start:.2f}s")
        return result
    return wrapper

@timer
def train_model():
    ...
```

## Generators

```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# Memory efficient — generates values on demand
gen = fibonacci()
first_10 = [next(gen) for _ in range(10)]
```

## Error Handling

```python
try:
    result = risky_operation()
except ValueError as e:
    print(f"Bad value: {e}")
except (TypeError, KeyError):
    print("Type or key error")
except Exception as e:
    print(f"Unexpected: {e}")
else:
    print("No errors!")
finally:
    cleanup()
```

## F-Strings

```python
name, score = "Model", 0.9543
print(f"{name}: {score:.2%}")      # Model: 95.43%
print(f"{score:.4f}")              # 0.9543
print(f"{'centered':^20}")        # "     centered      "
print(f"{1000000:,}")             # 1,000,000
```

## Common Pitfalls

| Pitfall | Wrong | Right |
|---------|-------|-------|
| Mutable default | `def f(lst=[])` | `def f(lst=None)` |
| Copy vs reference | `b = a` | `b = a.copy()` |
| String comparison | `s == "yes" or "no"` | `s in ("yes", "no")` |
