## Django Async Framework

DAF is a modern asynchronous framework built on top of Django, designed to support fully async class-based views, async-safe ORM operations, background tasks, async error handling, rate limiting, and more, all aimed at making Django better suited for high-concurrency APIs.

<p>
  <a href="https://github.com/mouhamaddev/django-async-framework" style="text-decoration:none;">
    <button style="padding:10px 15px; font-size:14px; color:white; background-color:#007BFF; border:none; border-radius:5px; cursor:pointer;">
      Check it out on GitHub &nbsp; 🔗
    </button>
  </a>
</p>

<p>
  <a href="https://pypi.org/project/djangoasyncframework/" style="text-decoration:none;">
    <button style="padding:10px 15px; font-size:14px; color:white; background-color:#007BFF; border:none; border-radius:5px; cursor:pointer;">
      Check it out on PyPI &nbsp; 📦
    </button>
  </a>
</p>

<br>

*Below are some notes I add whenever I learn something new during the development process:*

<br>

Date: 15-5-2025

Today I Learned:
- dispatch() is the method that routes the request to get(), post(), or whatever the method was.
- If I want to handle something no matter what HTTP method is used then I should overrite dispatch().
- View class (django.views) does two core thigs:
    - as_view() Method: Converts a class into a callable view function to be used in urls.py.
    - dispatch(): Routes request to the correct HTTP method.


Date: 16-5-2025

Today I Learned:
- Learned how to write a simple function-based middleware.


Date: 17-5-2025

Today I Learned:
- That feeling overwhelmed while building something like this is completely normal, in fact, it’s a sign that I’m working on something meaningful :D.


Date: 20-5-2025

Today I Learned:
- Django’s built-in throttling (via DRF) is sync-based and tied to DRF.


Date: 21-5-2025

Today I Learned:
- That integrating throttling into AsyncAPIView requires hooking into the dispatch() method before the actual view handler is called to ensure rate limits being enforced before any expensive logic runs.


Date: 23-5-2025

Today I Learned:
- Using requests.get(...) in Django views blocks the thread; better async alternatives exist.
- WSGI vs ASGI:
  - WSGI: Only supports synchronous code; one request per worker at a time.
  - ASGI: Supports both sync and async which makes it ideal for WebSockets and long-lived connections.
- Web Server Layers:
  1. Web Server(Nginx/Apache): Handles SSL, load balancing.
  2. Application Server(Gunicorn/Uvicorn): Runs Django workers.
  3. Interface Layer(WSGI/ASGI): Protocol layer translating requests between server and Django.
  4. App Layer(Django): Executes the actual application logic.
- Gunicorn + WSGI: Multiple workers, each handling one request at a time.
- Uvicorn + ASGI: Event loop handles many I/O-bound tasks concurrently.
- Async Use Cases:
  - Ideal for fast and concurrent I/O-bound tasks (e.g., multiple API calls).
  - Useful when we want lower latency and minimal infrastructure overhead.
  - Not a replacement for background tasks like Celery.
- When to Use Celery + Redis:
  - Long-running or compute-heavy tasks.
  - Jobs needing retries, scheduling, or chaining.
  - Tasks needing decoupled processing and independent scaling.
- Django Channels:
  - Good for WebSockets, long-lived bi-directional connections (e.g., chat apps).
  - Not a replacement for async views as they serve different purposes.
- ASGI/WSGI are interface standards (also used in Flask).
- Async runs in a single thread using an event loop.
- CPUs with multiple cores can truly do tasks in parallel, threads switch between tasks.
- Async is concurrency, not true thread based parallelism.


Date: 26-5-2025

Today I Learned:
- That after creating my first AsyncView that requires developers to write async coroutines, I thought about an alternative approach: instead of forcing async usage, I’d automatically convert a regular handler into a coroutine by extending AsyncView. However, after testing it hands-on, it turned out that this approach isn’t ideal / safe because it still executes blocking code, defeating the whole purpose of async.