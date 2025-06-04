### Asynchronous Programming

#### async and await Syntax

- **`async def`**: Declares a coroutine function, which can use `await` to suspend its execution until the result of an asynchronous operation is available.
- **`await`**: Suspends the execution of the coroutine until the awaited coroutine or Future completes and returns the result.

```python
import asyncio

async def async_task():
    print("Task started")
    await asyncio.sleep(1)
    print("Task completed")

# Running an asynchronous coroutine
asyncio.run(async_task())
```

#### Asynchronous I/O Operations

Asynchronous I/O operations involve tasks that wait for external resources. Asyncio provides mechanisms to handle these operations efficiently without blocking the event loop.

##### Asynchronous HTTP Request with aiohttp

```python
import aiohttp
import asyncio

async def fetch_data(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.text()

async def main():
    url = 'https://jsonplaceholder.typicode.com/posts/1'
    response = await fetch_data(url)
    print(response)

asyncio.run(main())
```

- **`aiohttp.ClientSession`**: Manages HTTP connections and provides a context manager for making HTTP requests asynchronously.
- **`session.get(url)`**: Initiates an asynchronous GET request to the specified URL.
- **`response.text()`**: Asynchronously retrieves and returns the response body as text.

### Why do we use Async?

- Non-blocking operations allow other tasks to run while waiting for I/O.
- Handles large numbers of concurrent connections efficiently.
- Avoids callback-based programming with clearer syntax using `async` and `await`.
