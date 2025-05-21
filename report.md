# MonteCarioPi
## Was the multi-threaded implementation always faster?

In my tests the multi-thread calculations where always about 4 times faster than without multi-thread
but in general No, not always.

## Why might it be slower?
- **Thread overhead:** Managing threads takes time.
- **CPU limits:** Too many threads can slow things down.
- **Uneven workload:** Some threads may do more work than others.

## How can you fix this?
- **Use fewer threads:** Match them to CPU cores.
- **Balance workload:** Ensure all threads get equal work.  

# Atomic Variables 
## 1
I ran this simple Java program with two threads that each count to 1,000,000 in two ways:

```
Atomic Counter: 2000000
Normal Counter: 1345789  // This will change every time
```
**Normal Counter** is less because threads overwrite each other’s updates
## 2
### Why `AtomicInteger`?

* It helps multiple threads change a number without messing it up
* It’s quick because it doesn’t use locks

## 3
 `atomicCounter.incrementAndGet()` means “add one and give me the new number” all at once.

1.The add happens in one step—no interruptions.
2.Once one thread updates, others see it .
3.Threads never wait for each other.

## 4
### When You’d Use a Lock Instead

* If you need to do several things in a row without other threads stepping in (check, then update)
* If threads need to wait for a condition and then be told to continue.

### Other Atomic Types in Java

* **`AtomicBoolean`**: for true/false values
* **`AtomicLong`**: same idea for long numbers
* **`AtomicReference<V>`**: for swapping object references safely
* **Atomic Arrays**: `AtomicIntegerArray`, `AtomicLongArray`, `AtomicReferenceArray<E>` for arrays

---





