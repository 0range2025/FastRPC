FastRPC

高性能的远程过程调用（RPC）框架，支持异步请求、负载均衡与服务治理，适用于分布式系统和微服务架构。
A high-performance RPC framework supporting asynchronous requests, load balancing, and service management, ideal for distributed systems and microservices.

目录 / Table of Contents

特性 / Features

安装 / Installation

快速开始 / Quick Start

架构设计 / Architecture

使用示例 / Examples

贡献 / Contributing

许可证 / License

特性 / Features

高性能 / High Performance：基于事件驱动和异步 IO，实现低延迟、高吞吐量的 RPC 调用

异步请求 / Async Calls：支持非阻塞调用，提升系统并发处理能力

服务注册与发现 / Service Registry & Discovery：方便微服务动态管理

负载均衡 / Load Balancing：多种策略支持，提升服务可用性

可扩展 / Extensible：模块化设计，便于自定义协议和传输层

安装 / Installation
# 克隆仓库
git clone https://github.com/yourusername/FastRPC.git
cd FastRPC

# 编译（假设使用 CMake）
mkdir build && cd build
cmake ..
make -j

快速开始 / Quick Start
启动服务端 / Server
#include "FastRPCServer.h"

int main() {
    FastRPCServer server("0.0.0.0", 50051);
    server.registerService<MyService>();
    server.start();
    return 0;
}

客户端调用 / Client
#include "FastRPCClient.h"

int main() {
    FastRPCClient client("127.0.0.1", 50051);
    auto result = client.call<MyService::Foo>("Hello RPC");
    std::cout << "Response: " << result << std::endl;
    return 0;
}

架构设计 / Architecture

网络层 / Network Layer：基于 Muduo 网络库，实现高性能 TCP 连接管理

序列化层 / Serialization：支持 Protobuf/JSON 等多种协议

服务管理 / Service Management：注册、发现、负载均衡

异步调用 / Async Call：事件驱动、线程池优化，高并发友好

架构示意图：

Client <-> Network Layer <-> Serialization <-> Service Management <-> Server

使用示例 / Examples

更多示例请见 /examples 目录，包含：

同步调用示例

异步调用示例

多服务注册与发现示例

