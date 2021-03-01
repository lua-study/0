# RESTvsGRPC
Evaluating Performance of REST vs. gRPC

## dotnet run -p RestAPI.csproj -c Release
Starts the ASP.NET MVC Core REST API

## dotnet run -p GrpcAPI.csproj -c Release
Starts the GRPC Service

## dotnet run -p RESTvsGRPC.csproj -c Release
Runs the benchmark on the above services

# Benchmark for .NET Core 3.1

``` ini

BenchmarkDotNet=v0.12.1, OS=Windows 10.0.18363.720 (1909/November2018Update/19H2)
Intel Core i7-8650U CPU 1.90GHz (Kaby Lake R), 1 CPU, 8 logical and 4 physical cores
.NET Core SDK=3.1.201
  [Host]     : .NET Core 3.1.3 (CoreCLR 4.700.20.11803, CoreFX 4.700.20.12001), X64 RyuJIT
  DefaultJob : .NET Core 3.1.3 (CoreCLR 4.700.20.11803, CoreFX 4.700.20.12001), X64 RyuJIT


```

|                         Method | IterationCount |        Mean |     Error |    StdDev |
|------------------------------- |--------------- |------------:|----------:|----------:|
|   **RestGetSmallPayloadAsync** |        **100** |**19.29 ms** |**0.351 ms** | **0.587 ms** |
|       RestGetLargePayloadAsync |            100 | 1,148.05 ms | 18.455 ms | 16.359 ms |
|      RestPostLargePayloadAsync |            100 | 1,424.61 ms | 12.557 ms | 11.131 ms |
|       GrpcGetSmallPayloadAsync |            100 |    27.04 ms |  0.197 ms |  0.175 ms |
|    GrpcStreamLargePayloadAsync |            100 | 2,183.97 ms | 30.565 ms | 27.095 ms |
| GrpcGetLargePayloadAsListAsync |            100 |   222.20 ms |  4.219 ms |  5.022 ms |
|      GrpcPostLargePayloadAsync |            100 |   228.69 ms |  4.411 ms |  4.529 ms |
|   **RestGetSmallPayloadAsync** |        **200** |   **39.84 ms** |  **0.334 ms** |  **0.261 ms** |
|       RestGetLargePayloadAsync |            200 | 2,504.54 ms | 47.424 ms | 48.701 ms |
|      RestPostLargePayloadAsync |            200 | 2,935.26 ms | 29.985 ms | 26.580 ms |
|       GrpcGetSmallPayloadAsync |            200 |    60.82 ms |  1.070 ms |  1.001 ms |
|    GrpcStreamLargePayloadAsync |            200 | 4,826.83 ms | 38.930 ms | 34.510 ms |
| GrpcGetLargePayloadAsListAsync |            200 |   447.88 ms |  8.778 ms |  8.211 ms |
|      GrpcPostLargePayloadAsync |            200 |   464.99 ms |  9.254 ms |  9.902 ms |




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)