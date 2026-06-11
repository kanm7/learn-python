#### Lock的用法

```python
import threading
import time

count = 0

lock = threading.Lock()

def add(name):
    global count

    for _ in range(5):
        with lock:
            print(f"{name}第{_}次执行开始")
            count += 1
            print(f"{name}第{_}次执行结束")

threads = []

for i in range(2):
    t = threading.Thread(target=add, args=(f"线程{i+1}", ))
    threads.append(t)
    t.start()

for i in range(2):
    threads[i].join()

print("主线程执行结束")


```

#### Semaphore用法

```python
import threading

sem_a = threading.Semaphore(1)
sem_b = threading.Semaphore(0)
sem_c = threading.Semaphore(0)

def print_a():
    for _ in range(2):
        sem_a.acquire()
        print("A", end="")
        sem_b.release()

def print_b():
    for _ in range(2):
        sem_b.acquire()
        print("B", end="")
        sem_c.release()

def print_c():
    for _ in range(2):
        sem_c.acquire()
        print("C", end="")
        sem_a.release()

t1 = threading.Thread(target=print_a)
t2 = threading.Thread(target=print_b)
t3 = threading.Thread(target=print_c)

t1.start()
t2.start()
t3.start()

t1.join()
t2.join()
t3.join()
```

