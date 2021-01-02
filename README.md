This is a setup for Libtorch debug version for Windows.

I setup on CLion with Windows MSVC compiler (x64) and working fine with CUDA 10.1.

> After painfully figuring out WTF is going on with the library.  
> [This blog post](https://blog.csdn.net/XDH19910113/article/details/110072837) was helpful when I was figuring out what's wrong with the setup.

Also if you are trying to use Libtorch in Windows, just use MSVC do not use MinGW unless you want to compile the Libtorch from source by yourself.  
I saw the github issue when I was googling but I lost it now. (will link it when I found it again).

And if you downloaded release version of Libtorch, you will need to update your cmake options. Check the official documentation about that.
