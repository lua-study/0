 

 
 
SixLabors.ImageSharp
 


 

[![Build Status](https://img.shields.io/github/workflow/status/SixLabors/ImageSharp/Build/master)](https://github.com/SixLabors/ImageSharp/actions)
[![Code coverage](https://codecov.io/gh/SixLabors/ImageSharp/branch/master/graph/badge.svg)](https://codecov.io/gh/SixLabors/ImageSharp)
[![GitHub license](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://raw.githubusercontent.com/SixLabors/ImageSharp/master/LICENSE)
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/ImageSharp/General?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Twitter](https://img.shields.io/twitter/url/http/shields.io.svg?style=flat&logo=twitter)](https://twitter.com/intent/tweet?hashtags=imagesharp,dotnet,oss&text=ImageSharp.+A+new+cross-platform+2D+graphics+API+in+C%23&url=https%3a%2f%2fgithub.com%2fSixLabors%2fImageSharp&via=sixlabors)
[![OpenCollective](https://opencollective.com/imagesharp/backers/badge.svg)](#backers)
[![OpenCollective](https://opencollective.com/imagesharp/sponsors/badge.svg)](#sponsors)

 

### **ImageSharp** is a new, fully featured, fully managed, cross-platform, 2D graphics API. 

Designed to democratize image processing, ImageSharp brings you an incredibly powerful yet beautifully simple API.

Compared to `System.Drawing` we have been able to develop something much more flexible, easier to code against, and much, much less prone to memory leaks. Gone are system-wide process-locks; ImageSharp images are thread-safe and fully supported in web environments.

Built against .NET Standard 1.3, ImageSharp can be used in device, cloud, and embedded/IoT scenarios. 

### Documentation
For all SixLabors projects, including ImageSharp:
https://sixlabors.github.io/docs/

### Installation

Install stable releases via Nuget; development releases are available via MyGet.

| Package Name                   | Release (NuGet) | Nightly (MyGet) |
|--------------------------------|-----------------|-----------------|
| `SixLabors.ImageSharp`         | [![NuGet](https://img.shields.io/nuget/v/SixLabors.ImageSharp.svg)](https://www.nuget.org/packages/SixLabors.ImageSharp/) | [![MyGet](https://img.shields.io/myget/sixlabors/v/SixLabors.ImageSharp.svg)](https://www.myget.org/feed/sixlabors/package/nuget/SixLabors.ImageSharp) |

### Packages

The **ImageSharp** library is made up of multiple packages:
- **SixLabors.ImageSharp**
  - Contains the generic `Image ` class, PixelFormats, Primitives, Configuration, and other core functionality
  - The `IImageFormat` interface, Jpeg, Png, Bmp, and Gif formats
  - Transform methods like Resize, Crop, Skew, Rotate - anything that alters the dimensions of the image
  - Non-transform methods like Gaussian Blur, Pixelate, Edge Detection - anything that maintains the original image dimensions

### Questions?

- Do you have questions? We are happy to help! Please [join our gitter channel](https://gitter.im/ImageSharp/General), or ask them on [stackoverflow](https://stackoverflow.com) using the `ImageSharp` tag. **Do not** open issues for questions!
- Please read our [Contribution Guide](https://github.com/SixLabors/ImageSharp/blob/master/.github/CONTRIBUTING.md) before opening issues or pull requests!

### Code of Conduct  
This project has adopted the code of conduct defined by the [Contributor Covenant](https://contributor-covenant.org/) to clarify expected behavior in our community.
For more information, see the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).

### API 

Our API is designed to be simple to consume. Here's an example of the code required to resize an image using the default Bicubic resampler then turn the colors into their grayscale equivalent using the BT709 standard matrix.

On platforms supporting netstandard 1.3+

```csharp
using SixLabors.ImageSharp;
using SixLabors.ImageSharp.Processing;
using SixLabors.ImageSharp.PixelFormats;

// Image.Load(string path) is a shortcut for our default type. 
// Other pixel formats use Image.Load (string path))
using (Image image = Image.Load("foo.jpg"))
{
    image.Mutate(x => x
         .Resize(image.Width / 2, image.Height / 2)
         .Grayscale());
    image.Save("bar.jpg"); // Automatic encoder selected based on extension.
}
```

Setting individual pixel values can be performed as follows:

```csharp
using SixLabors.ImageSharp;
using SixLabors.ImageSharp.PixelFormats;

// Individual pixels
using (var image = new Image (400, 400))
{
    image[200, 200] = Rgba32.White;
}
```

`Rgba32` is our default PixelFormat, equivalent to `System.Drawing Color`. For advanced pixel format usage there are multiple [PixelFormat implementations](https://github.com/SixLabors/ImageSharp/tree/master/src/ImageSharp/PixelFormats) available allowing developers to implement their own color models in the same manner as Microsoft XNA Game Studio and MonoGame. 

For more examples check out: 
- [Our Documentation](https://sixlabors.github.io/docs/)
- Our [Samples Repository](https://github.com/SixLabors/Samples/tree/master/ImageSharp)
- The [beta1 blog post](https://sixlabors.com/blog/announcing-imagesharp-beta-1/)

### Manual build

If you prefer, you can compile ImageSharp yourself (please do and help!)

- Using [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)
  - Make sure you have the latest version installed
  - Make sure you have [the .NET Core 3.1 SDK](https://www.microsoft.com/net/core#windows) installed

Alternatively, you can work from command line and/or with a lightweight editor on **both Linux/Unix and Windows**:

- [Visual Studio Code](https://code.visualstudio.com/) with [C# Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- [.NET Core](https://www.microsoft.com/net/core#linuxubuntu)

To clone ImageSharp locally, click the "Clone in [YOUR_OS]" button above or run the following git commands:

```bash
git clone https://github.com/SixLabors/ImageSharp
```

If working with Windows please ensure that you have enabled log file paths in git (run as Administrator).

```bash
git config --system core.longpaths true
```

### Submodules

This repository contains [git submodules](https://blog.github.com/2016-02-01-working-with-submodules/). To add the submodules to the project, navigate to the repository root and type:

``` bash
git submodule update --init --recursive
```

### How can you help?

Please... Spread the word, contribute algorithms, submit performance improvements, unit tests, no input is too little. Make sure to read our [Contribution Guide](https://github.com/SixLabors/ImageSharp/blob/master/.github/CONTRIBUTING.md) before opening a PR.

### The ImageSharp Team

Grand High Eternal Dictator
- [James Jackson-South](https://github.com/jimbobsquarepants)

Core Team
- [Dirk Lemstra](https://github.com/dlemstra)
- [Anton Firsov](https://github.com/antonfirsov)
- [Scott Williams](https://github.com/tocsoft)
- [Brian Popow](https://github.com/brianpopow)

### Backers

Support us with a monthly donation and help us continue our activities. [[Become a backer](https://opencollective.com/imagesharp#backer)]

   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   

### Sponsors

Become a sponsor and get your logo on our README on Github with a link to your site. [[Become a sponsor](https://opencollective.com/imagesharp#sponsor)]

   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)