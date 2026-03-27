# DelegateMQ

**DelegateMQ** is a C++17 header-only messaging library for invoking any callable — function, method, or lambda — synchronously, asynchronously, or remotely across threads, processes, and processors.

[![License MIT](https://img.shields.io/github/license/DelegateMQ/DelegateMQ?color=blue)](https://github.com/DelegateMQ/DelegateMQ/blob/master/LICENSE)
[![Ubuntu](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_ubuntu.yml/badge.svg)](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_ubuntu.yml)
[![Windows](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_windows.yml/badge.svg)](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_windows.yml)
[![Clang](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_clang.yml/badge.svg)](https://github.com/DelegateMQ/DelegateMQ/actions/workflows/cmake_clang.yml)
![C++17](https://img.shields.io/badge/C%2B%2B-17-blue)
![Header Only](https://img.shields.io/badge/header--only-yes-brightgreen)
![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20Linux%20%7C%20RTOS%20%7C%20Bare--Metal-informational)
## What It Does

| Feature | Description |
|---------|-------------|
| **Synchronous Delegates** | Type-safe callable wrappers — free functions, members, lambdas |
| **Asynchronous Delegates** | Fire-and-forget or blocking dispatch to any worker thread |
| **Signal & Slot** | Thread-safe multicast with RAII `ScopedConnection` handles |
| **DataBus** | Topic-based publish/subscribe across threads or network nodes |
| **Remote Delegates** | Inter-process and inter-processor messaging over any transport |

## Repositories

| Repository | Description |
|------------|-------------|
| [DelegateMQ](https://github.com/DelegateMQ/DelegateMQ) | Core library — delegates, signals, DataBus, diagnostic tools |
| [IntegrationTestFramework](https://github.com/DelegateMQ/IntegrationTestFramework) | Multi-threaded C++ integration test framework using DelegateMQ |
| [active-fsm](https://github.com/DelegateMQ/active-fsm) | Active-object C++ finite state machine with async dispatch and pub/sub signals |
| [Async-SQLite](https://github.com/DelegateMQ/Async-SQLite) | Asynchronous thread-safe SQLite wrapper using DelegateMQ |
| [Async-DuckDB](https://github.com/DelegateMQ/Async-DuckDB) | Asynchronous thread-safe DuckDB wrapper using DelegateMQ |

## Quick Example

```cpp
#include "DelegateMQ.h"

// Synchronous
auto d = MakeDelegate(&MyClass::Func, &obj);
d(arg);

// Async — dispatched to workerThread
auto d = MakeDelegate(&MyClass::Func, &obj, workerThread);
d(arg);

// Signal & Slot
Signal<void(int)> signal;
auto conn = signal.Connect(MakeDelegate(&MyClass::OnEvent, &obj));
signal(42);  // invokes all connected slots
```

## Platforms

Works on Windows, Linux, and a wide range of embedded targets including FreeRTOS, ThreadX, Zephyr, CMSIS-RTOS2, and bare-metal ARM. Transport backends include ZeroMQ, NNG, MQTT, TCP, UDP, serial, and more.

## Get Started

```bash
git clone https://github.com/DelegateMQ/DelegateMQ.git
```

See the [documentation](https://github.com/DelegateMQ/DelegateMQ/blob/master/docs/DETAILS.md) for full details.
