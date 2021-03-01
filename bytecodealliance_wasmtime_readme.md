 
    wasmtime  

   
     A standalone runtime for
     WebAssembly  
   

   A  Bytecode Alliance  project 

   
       
       
     
       
   

   
     Guide 
      |  
     Contributing 
      |  
     Website 
      |  
     Chat 
   
 

## Installation

The Wasmtime CLI can be installed on Linux and macOS with a small install
script:

```sh
$ curl https://wasmtime.dev/install.sh -sSf | bash
```

Windows or otherwise interested users can download installers and
binaries directly from the [GitHub
Releases](https://github.com/bytecodealliance/wasmtime/releases) page.

## Example

If you've got the [Rust compiler
installed](https://www.rust-lang.org/tools/install) then you can take some Rust
source code:

```rust
fn main() {
    println!("Hello, world!");
}
```

and compile/run it with:

```sh
$ rustup target add wasm32-wasi
$ rustc hello.rs --target wasm32-wasi
$ wasmtime hello.wasm
Hello, world!
```

## Features

* **Lightweight**. Wasmtime is a standalone runtime for WebAssembly that scales
  with your needs. It fits on tiny chips as well as makes use of huge servers.
  Wasmtime can be [embedded] into almost any application too.

* **Fast**. Wasmtime is built on the optimizing [Cranelift] code generator to
  quickly generate high-quality machine code at runtime.

* **Configurable**. Whether you need to precompile your wasm ahead of time,
  generate code blazingly fast with Lightbeam, or interpret it at runtime,
  Wasmtime has you covered for all your wasm-executing needs.

* **WASI**. Wasmtime supports a rich set of APIs for interacting with the host
  environment through the [WASI standard](https://wasi.dev).

* **Standards Compliant**. Wasmtime passes the [official WebAssembly test
  suite](https://github.com/WebAssembly/testsuite), implements the [official C
  API of wasm](https://github.com/WebAssembly/wasm-c-api), and implements
  [future proposals to WebAssembly](https://github.com/WebAssembly/proposals) as
  well. Wasmtime developers are intimately engaged with the WebAssembly
  standards process all along the way too.

[Cranelift]: https://github.com/bytecodealliance/wasmtime/blob/master/cranelift/README.md
[embedded]: https://bytecodealliance.github.io/wasmtime/lang.html

## Language Support

You can use Wasmtime from a variety of different languages through embeddings of
the implementation:

* **[Rust]** - the [`wasmtime` crate]
* **[C]** - the [`wasm.h`], [`wasi.h`], and [`wasmtime.h`] headers
* **[Python]** - the [`wasmtime` PyPI package]
* **[.NET]** - the [`Wasmtime` NuGet package]
* **[Go]** - the [wasmtime-go repository]

[Rust]: https://bytecodealliance.github.io/wasmtime/lang-rust.html
[C]: https://bytecodealliance.github.io/wasmtime/examples-c-embed.html
[`wasmtime` crate]: https://crates.io/crates/wasmtime
[`wasm.h`]: https://github.com/WebAssembly/wasm-c-api/blob/master/include/wasm.h
[`wasi.h`]: https://github.com/bytecodealliance/wasmtime/blob/master/crates/c-api/include/wasi.h
[`wasmtime.h`]: https://github.com/bytecodealliance/wasmtime/blob/master/crates/c-api/include/wasmtime.h
[Python]: https://bytecodealliance.github.io/wasmtime/lang-python.html
[`wasmtime` PyPI package]: https://pypi.org/project/wasmtime/
[.NET]: https://bytecodealliance.github.io/wasmtime/lang-dotnet.html
[`Wasmtime` NuGet package]: https://www.nuget.org/packages/Wasmtime
[Go]: https://bytecodealliance.github.io/wasmtime/lang-go.html
[wasmtime-go repository]: https://pkg.go.dev/github.com/bytecodealliance/wasmtime-go

## Documentation

[📚 Read the Wasmtime guide here! 📚][guide]

The [wasmtime guide][guide] is the best starting point to learn about what
Wasmtime can do for you or help answer your questions about Wasmtime. If you're
curious in contributing to Wasmtime, [it can also help you do
that][contributing]!.

[contributing]: https://bytecodealliance.github.io/wasmtime/contributing.html
[guide]: https://bytecodealliance.github.io/wasmtime

---

It's Wasmtime.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)