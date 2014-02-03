---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [intro, beginner, jekyll, tutorial]
---

Github+Jekyll
====================
********************
* ##_安装jekyll_

###_1.安装RubyInstaller和DevKit_

进入DevKit安装目录运行如下命令

    ruby dk.rb init
    ruby dk.rb install
    
###_2.更换淘宝的源_

运行如下命令

    $ gem sources --remove http://rubygems.org/
    $ gem sources -a http://ruby.taobao.org/
    $ gem sources -l
    *** CURRENT SOURCES ***
        
    http://ruby.taobao.org
    # 请确保只有 ruby.taobao.org
    $ gem install jekyll

参考链接：[RubyGems 镜像 - 淘宝网](http://ruby.taobao.org/)
    
###_3.安装效率更好的模版解释器_

默认的``Maruku``是纯ruby的Markdown模版解释器，而``RDiscount``则是c写的模版解释器，效率更好。可以参考如下别人做的对比

> BlueCloth: 13.029987s total time, 00.130300s average   
> Maruku: 08.424132s total time, 00.084241s average   
> RDiscount: 00.082019s total time, 00.000820s average   

运行以下命令安装

    gem install RDiscount

然后在你站点下的``_config.yml``文件中加入以下配置

    markdown: rdiscount

###_4.更改环境变量以支持生成有中文的文章_

打开计算机–属性–高级系统设置–环境变量，新增``LANG``和``LC_ALL``，值都是``zh_CN.UTF-8``，完成后确定保存

###_5.运行Jekyll_

    jekyll serve --watch #不加--watch则不会检测文件夹内的变化，即修改后需要重新启动jekyll

然后浏览localhost:4000就可以看到页面了。


    E:\Programs\DevKit>ruby dk.rb init
    [INFO] found RubyInstaller v1.9.3 at E:/Programs/Ruby193
    
    Initialization complete! Please review and modify the auto-generated
    'config.yml' file to ensure it contains the root directories to all
    of the installed Rubies you want enhanced by the DevKit.
    
    E:\Programs\DevKit>ruby dk.rb install
    [INFO] Updating convenience notice gem override for 'E:/Programs/Ruby193'
    [INFO] Installing 'E:/Programs/Ruby193/lib/ruby/site_ruby/devkit.rb'
    
    E:\Programs\DevKit>ruby dk.rb review
    Based upon the settings in the 'config.yml' file generated
    from running 'ruby dk.rb init' and any of your customizations,
    DevKit functionality will be injected into the following Rubies
    when you run 'ruby dk.rb install'.
    
    E:/Programs/Ruby193
    
    E:\Programs\DevKit>gem install rdiscount --platform=ruby
    Fetching: rdiscount-2.1.7.gem (100%)
    Temporarily enhancing PATH to include DevKit...
    Building native extensions.  This could take a while...
    Successfully installed rdiscount-2.1.7
    1 gem installed
    Installing ri documentation for rdiscount-2.1.7...
    Installing RDoc documentation for rdiscount-2.1.7...
    
    E:\Programs\DevKit>

-------------------------------------------------------------

    Microsoft Windows [版本 6.1.7601]
    版权所有 (c) 2009 Microsoft Corporation。保留所有权利。
    
    C:\Users\FCX>gem sources -l
    *** CURRENT SOURCES ***
    
    http://rubygems.org/
    
    C:\Users\FCX>gem sources --remove http://rubygems.org/
    http://rubygems.org/ removed from sources
    
    C:\Users\FCX>gem sources -l
    *** CURRENT SOURCES ***
    
    
    C:\Users\FCX>gem sources -a http://ruby.taobao.org/
    http://ruby.taobao.org/ added to sources
    
    C:\Users\FCX>gem sources -l
    *** CURRENT SOURCES ***
    
    http://ruby.taobao.org/
    
    C:\Users\FCX>gem install jekyll
    Fetching: liquid-2.5.5.gem (100%)
    Fetching: fast-stemmer-1.0.2.gem (100%)
    Temporarily enhancing PATH to include DevKit...
    Building native extensions.  This could take a while...
    Fetching: classifier-1.3.4.gem (100%)
    Fetching: rb-fsevent-0.9.4.gem (100%)
    Fetching: ffi-1.9.3-x86-mingw32.gem (100%)
    Fetching: rb-inotify-0.9.3.gem (100%)
    Fetching: rb-kqueue-0.2.0.gem (100%)
    Fetching: listen-1.3.1.gem (100%)
    Fetching: maruku-0.7.1.gem (100%)
    Fetching: yajl-ruby-1.1.0-x86-mingw32.gem (100%)
    Fetching: posix-spawn-0.3.8.gem (100%)
    Building native extensions.  This could take a while...
    Fetching: pygments.rb-0.5.4.gem (100%)
    Fetching: highline-1.6.20.gem (100%)
    Fetching: commander-4.1.5.gem (100%)
    Fetching: safe_yaml-0.9.7.gem (100%)
    Fetching: colorator-0.1.gem (100%)
    Fetching: redcarpet-2.3.0.gem (100%)
    Building native extensions.  This could take a while...
    Fetching: blankslate-2.1.2.4.gem (100%)
    Fetching: parslet-1.5.0.gem (100%)
    Fetching: toml-0.1.0.gem (100%)
    Fetching: jekyll-1.4.3.gem (100%)
    Successfully installed liquid-2.5.5
    Successfully installed fast-stemmer-1.0.2
    Successfully installed classifier-1.3.4
    Successfully installed rb-fsevent-0.9.4
    Successfully installed ffi-1.9.3-x86-mingw32
    Successfully installed rb-inotify-0.9.3
    Successfully installed rb-kqueue-0.2.0
    Successfully installed listen-1.3.1
    Successfully installed maruku-0.7.1
    Successfully installed yajl-ruby-1.1.0-x86-mingw32
    Successfully installed posix-spawn-0.3.8
    Successfully installed pygments.rb-0.5.4
    Successfully installed highline-1.6.20
    Successfully installed commander-4.1.5
    Successfully installed safe_yaml-0.9.7
    Successfully installed colorator-0.1
    Successfully installed redcarpet-2.3.0
    Successfully installed blankslate-2.1.2.4
    Successfully installed parslet-1.5.0
    Successfully installed toml-0.1.0
    Successfully installed jekyll-1.4.3
    21 gems installed
    Installing ri documentation for liquid-2.5.5...
    Installing ri documentation for fast-stemmer-1.0.2...
    Installing ri documentation for classifier-1.3.4...
    Installing ri documentation for rb-fsevent-0.9.4...
    Installing ri documentation for ffi-1.9.3-x86-mingw32...
    Enclosing class/module 'moduleFFI' for class AbstractMemory not known
    Enclosing class/module 'moduleFFI' for class NullPointerError not known
    Enclosing class/module "classMemory" for alias put_" #name, "put_" #old); \
        rb_define_alias(classMemory, "get_" #name, "get_" #old); \
        rb_define_alias(classMemory, "put_u" #name, "put_u" #old); \
        rb_define_alias(classMemory, "get_u" #name, "get_u" #old); \
        rb_define_alias(classMemory, "write_" #name, "write_" #old); \
        rb_define_alias(classMemory, "read_" #name, "read_" #old); \
        rb_define_alias(classMemory, "write_u" #name, "write_u" #old); \
        rb_define_alias(classMemory, "read_u" #name, "read_u" #old); \
        rb_define_alias(classMemory, "put_array_of_" #name, "put_array_of_" #old); \
    
        rb_define_alias(classMemory, "get_array_of_" #name, "get_array_of_" #old); \
    
        rb_define_alias(classMemory, "put_array_of_u" #name, "put_array_of_u" #old);
     \
        rb_define_alias(classMemory, "get_array_of_u" #name, "get_array_of_u" #old);
     \
        rb_define_alias(classMemory, "write_array_of_" #name, "write_array_of_" #old
    ); \
        rb_define_alias(classMemory, "read_array_of_" #name, "read_array_of_" #old);
     \
        rb_define_alias(classMemory, "write_array_of_u" #name, "write_array_of_u" #o
    ld); \
        rb_define_alias(classMemory, "read_array_of_u" #name, "read_array_of_u" #old
    );
    
        ALIAS(char, int8);
        ALIAS(short, int16);
        ALIAS(int, int32);
        ALIAS(long_long, int64);
    
        /*
         * Document-method: put_float32
         * call-seq: memory.put_float32offset, value)
         * @param [Numeric] offset
         * @param [Numeric] value
         * @return [self]
         * Put +value+ as a 32-bit float in memory at offset +offset+ (alias: #put_f
    loat).
         */
        rb_define_method(classMemory, "put_float32", memory_put_float32, 2);
        /*
         * Document-method: get_float32
         * call-seq: memory.get_float32(offset)
         * @param [Numeric] offset
         * @return [Float]
         * Get a 32-bit float from memory at offset +offset+ (alias: #get_float).
         */
        rb_define_method(classMemory, "get_float32", memory_get_float32, 1);
        rb_define_alias(classMemory, "put_float put_float32 not known
    Enclosing class/module "classMemory" for alias get_float get_float32 not known
    Enclosing class/module "classMemory" for alias put_array_of_float put_array_of_f
    loat32 not known
    Enclosing class/module "classMemory" for alias get_array_of_float get_array_of_f
    loat32 not known
    Enclosing class/module "classMemory" for alias put_double put_float64 not known
    Enclosing class/module "classMemory" for alias get_double get_float64 not known
    Enclosing class/module "classMemory" for alias put_array_of_double put_array_of_
    float64 not known
    Enclosing class/module "classMemory" for alias get_array_of_double get_array_of_
    float64 not known
    Enclosing class/module "classMemory" for alias size total not known
    Enclosing class/module 'moduleFFI' for class ArrayType not known
    Enclosing class/module 'moduleFFI' for class Buffer not known
    Enclosing class/module "BufferClass" for alias length total not known
    Enclosing class/module 'moduleFFI' for module DataConverter not known
    Enclosing class/module 'moduleFFI' for class DynamicLibrary not known
    Enclosing class/module 'LibraryClass' for class Symbol not known
    Enclosing class/module 'rbffi_TypeClass' for class Mapped not known
    Enclosing class/module 'rbffi_StructLayoutClass' for class CharArray not known
    Enclosing class/module "rbffi_StructLayoutCharArrayClass" for alias to_str to_s
    not known
    Installing ri documentation for rb-inotify-0.9.3...
    Installing ri documentation for rb-kqueue-0.2.0...
    Installing ri documentation for listen-1.3.1...
    Installing ri documentation for maruku-0.7.1...
    Installing ri documentation for yajl-ruby-1.1.0-x86-mingw32...
    Installing ri documentation for posix-spawn-0.3.8...
    Installing ri documentation for pygments.rb-0.5.4...
    Installing ri documentation for highline-1.6.20...
    Installing ri documentation for commander-4.1.5...
    Installing ri documentation for safe_yaml-0.9.7...
    Installing ri documentation for colorator-0.1...
    Installing ri documentation for redcarpet-2.3.0...
    Installing ri documentation for blankslate-2.1.2.4...
    Installing ri documentation for parslet-1.5.0...
    Installing ri documentation for toml-0.1.0...
    Installing ri documentation for jekyll-1.4.3...
    Installing RDoc documentation for liquid-2.5.5...
    Installing RDoc documentation for fast-stemmer-1.0.2...
    Installing RDoc documentation for classifier-1.3.4...
    Installing RDoc documentation for rb-fsevent-0.9.4...
    Installing RDoc documentation for ffi-1.9.3-x86-mingw32...
    Enclosing class/module 'moduleFFI' for class AbstractMemory not known
    Enclosing class/module 'moduleFFI' for class NullPointerError not known
    Enclosing class/module "classMemory" for alias put_" #name, "put_" #old); \
        rb_define_alias(classMemory, "get_" #name, "get_" #old); \
        rb_define_alias(classMemory, "put_u" #name, "put_u" #old); \
        rb_define_alias(classMemory, "get_u" #name, "get_u" #old); \
        rb_define_alias(classMemory, "write_" #name, "write_" #old); \
        rb_define_alias(classMemory, "read_" #name, "read_" #old); \
        rb_define_alias(classMemory, "write_u" #name, "write_u" #old); \
        rb_define_alias(classMemory, "read_u" #name, "read_u" #old); \
        rb_define_alias(classMemory, "put_array_of_" #name, "put_array_of_" #old); \
    
        rb_define_alias(classMemory, "get_array_of_" #name, "get_array_of_" #old); \
    
        rb_define_alias(classMemory, "put_array_of_u" #name, "put_array_of_u" #old);
     \
        rb_define_alias(classMemory, "get_array_of_u" #name, "get_array_of_u" #old);
     \
        rb_define_alias(classMemory, "write_array_of_" #name, "write_array_of_" #old
    ); \
        rb_define_alias(classMemory, "read_array_of_" #name, "read_array_of_" #old);
     \
        rb_define_alias(classMemory, "write_array_of_u" #name, "write_array_of_u" #o
    ld); \
        rb_define_alias(classMemory, "read_array_of_u" #name, "read_array_of_u" #old
    );
    
        ALIAS(char, int8);
        ALIAS(short, int16);
        ALIAS(int, int32);
        ALIAS(long_long, int64);
    
        /*
         * Document-method: put_float32
         * call-seq: memory.put_float32offset, value)
         * @param [Numeric] offset
         * @param [Numeric] value
         * @return [self]
         * Put +value+ as a 32-bit float in memory at offset +offset+ (alias: #put_f
    loat).
         */
        rb_define_method(classMemory, "put_float32", memory_put_float32, 2);
        /*
         * Document-method: get_float32
         * call-seq: memory.get_float32(offset)
         * @param [Numeric] offset
         * @return [Float]
         * Get a 32-bit float from memory at offset +offset+ (alias: #get_float).
         */
        rb_define_method(classMemory, "get_float32", memory_get_float32, 1);
        rb_define_alias(classMemory, "put_float put_float32 not known
    Enclosing class/module "classMemory" for alias get_float get_float32 not known
    Enclosing class/module "classMemory" for alias put_array_of_float put_array_of_f
    loat32 not known
    Enclosing class/module "classMemory" for alias get_array_of_float get_array_of_f
    loat32 not known
    Enclosing class/module "classMemory" for alias put_double put_float64 not known
    Enclosing class/module "classMemory" for alias get_double get_float64 not known
    Enclosing class/module "classMemory" for alias put_array_of_double put_array_of_
    float64 not known
    Enclosing class/module "classMemory" for alias get_array_of_double get_array_of_
    float64 not known
    Enclosing class/module "classMemory" for alias size total not known
    Enclosing class/module 'moduleFFI' for class ArrayType not known
    Enclosing class/module 'moduleFFI' for class Buffer not known
    Enclosing class/module "BufferClass" for alias length total not known
    Enclosing class/module 'moduleFFI' for module DataConverter not known
    Enclosing class/module 'moduleFFI' for class DynamicLibrary not known
    Enclosing class/module 'LibraryClass' for class Symbol not known
    Enclosing class/module 'rbffi_TypeClass' for class Mapped not known
    Enclosing class/module 'rbffi_StructLayoutClass' for class CharArray not known
    Enclosing class/module "rbffi_StructLayoutCharArrayClass" for alias to_str to_s
    not known
    Installing RDoc documentation for rb-inotify-0.9.3...
    Installing RDoc documentation for rb-kqueue-0.2.0...
    Installing RDoc documentation for listen-1.3.1...
    Installing RDoc documentation for maruku-0.7.1...
    Installing RDoc documentation for yajl-ruby-1.1.0-x86-mingw32...
    Installing RDoc documentation for posix-spawn-0.3.8...
    Installing RDoc documentation for pygments.rb-0.5.4...
    Installing RDoc documentation for highline-1.6.20...
    Installing RDoc documentation for commander-4.1.5...
    Installing RDoc documentation for safe_yaml-0.9.7...
    Installing RDoc documentation for colorator-0.1...
    Installing RDoc documentation for redcarpet-2.3.0...
    Installing RDoc documentation for blankslate-2.1.2.4...
    Installing RDoc documentation for parslet-1.5.0...
    Installing RDoc documentation for toml-0.1.0...
    Installing RDoc documentation for jekyll-1.4.3...
    
    C:\Users\FCX>




但安装rdiscount的时候遇到了问题,rdiscount 在ruby 1.9.2版本上有个bug https://github.com/rtomayko/rdiscount/issues/48.我是升级到 1.9.3才解决的。