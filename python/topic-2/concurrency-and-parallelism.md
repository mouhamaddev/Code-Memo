### Concurrency and Parallelism

**Concurrency** refers to the ability of a system to handle multiple tasks at once, making progress on more than one task in overlapping time periods. It is often used to design systems that can handle multiple inputs and outputs (I/O) efficiently, such as web servers handling multiple requests concurrently.

**Parallelism**, on the other hand, involves executing multiple tasks simultaneously, using multiple processors or cores. It focuses on improving computational speed by dividing tasks across different processing units.

### Threading vs. Multiprocessing

#### Threading

- **Definition**: Threads are lightweight subprocesses within a process that share the same memory space.
- **Concurrency**: Threads run concurrently within a single process and share resources like memory.
- **GIL (Global Interpreter Lock)**: In CPython, the GIL allows only one thread to execute Python bytecode at a time, limiting true parallelism.
- **Use Cases**: Suitable for I/O-bound tasks (e.g., network requests, file operations) where threads can wait for I/O without blocking other threads.

```python
import threading

def worker():
    print("Thread working...")

# Create a thread
thread = threading.Thread(target=worker)
# Start the thread
thread.start()
# Wait for the thread to complete
thread.join()
```

#### Multiprocessing

- **Definition**: Processes are independent units that run concurrently and have separate memory spaces.
- **Parallelism**: Utilizes multiple CPU cores effectively, as each process runs in its own memory space.
- **GIL**: Each process in multiprocessing has its own Python interpreter and GIL, allowing true parallelism for CPU-bound tasks.
- **Use Cases**: Ideal for CPU-bound tasks (e.g., intensive calculations, data processing) that benefit from parallel execution across multiple cores.

```python
import multiprocessing

def worker():
    print("Process working...")

# Create a process
process = multiprocessing.Process(target=worker)
# Start the process
process.start()
# Wait for the process to complete
process.join()
```
