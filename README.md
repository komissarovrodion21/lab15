## Laboratory work XV

Данная лабораторная работа посвещена изучению инструментов статического и динамического анализа кода

## Tasks

- [X] 1. Ознакомиться со ссылками учебного материала
- [X] 2. Используя **cpplint** провести анализ проекта на **C++**
- [X] 3. Используя **Cppcheck** провести анализ проекта на **C++**
- [X] 4. Используя **OCLint** провести анализ проекта на **C++**
- [X] 5. Используя **Valgrind** провести анализ проекта на **C++**
- [X] 6. Составить отчет и отправить ссылку личным сообщением в **Slack**

main.cpp:
```
// Copyright 2018 komissarovrodion21
#include <iostream>

int main() {
    std::cout << "Hello, World!\n";
    return 0;
}
```

1)Анализ через cpplint:
```
$ cpplint main.cpp
Done processing main.cpp
```

2)Анализ через cppcheck:
```
$ cppcheck main.cpp
Checking main.cpp ...
```
3)Анализ через Valgrind:
```
$ g++ main.cpp
MacBook-Pro-Rodion:1 rodionkomissarov$ valgrind --leak-check=yes -v ./a.out
==1649== Memcheck, a memory error detector
==1649== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==1649== Using Valgrind-3.14.0.GIT-f19a956e0a-20180123 and LibVEX; rerun with -h for copyright info
==1649== Command: ./a.out
==1649== 
--1649-- Valgrind options:
--1649--    --leak-check=yes
--1649--    -v
--1649-- Output from sysctl({CTL_KERN,KERN_VERSION}):
--1649--   Darwin Kernel Version 17.2.0: Fri Sep 29 18:27:05 PDT 2017; root:xnu-4570.20.62~3/RELEASE_X86_64
--1649-- Arch and hwcaps: AMD64, LittleEndian, amd64-cx16-lzcnt-rdtscp-sse3-avx-avx2-bmi
--1649-- Page sizes: currently 4096, max supported 4096
--1649-- Valgrind library directory: /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind
--1649-- ./a.out (rx at 0x100000000, rw at 0x100002000)
--1649--    reading syms   from primary file (7 4)
--1649-- run: /usr/bin/dsymutil "./a.out"
warning: no debug symbols in executable (-arch x86_64)
--1649--    dsyms= ./a.out.dSYM/Contents/Resources/DWARF/a.out
--1649-- /usr/lib/dyld (rx at 0x100004000, rw at 0x10004f000)
--1649--    reading syms   from primary file (5 1485)
--1649-- Scheduler: using generic scheduler lock implementation.
--1649-- Reading suppressions file: /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp
==1649== embedded gdbserver: reading from /var/folders/_h/_s8823mn7td_9nn82n32tr180000gn/T//vgdb-pipe-from-vgdb-to-1649-by-rodionkomissarov-on-???
==1649== embedded gdbserver: writing to   /var/folders/_h/_s8823mn7td_9nn82n32tr180000gn/T//vgdb-pipe-to-vgdb-from-1649-by-rodionkomissarov-on-???
==1649== embedded gdbserver: shared mem   /var/folders/_h/_s8823mn7td_9nn82n32tr180000gn/T//vgdb-pipe-shared-mem-vgdb-1649-by-rodionkomissarov-on-???
==1649== 
==1649== TO CONTROL THIS PROCESS USING vgdb (which you probably
==1649== don't want to do, unless you know exactly what you're doing,
==1649== or are doing some strange experiment):
==1649==   /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/../../bin/vgdb --pid=1649 ...command...
==1649== 
==1649== TO DEBUG THIS PROCESS USING GDB: start GDB like this
==1649==   /path/to/gdb ./a.out
==1649== and then give GDB the following command
==1649==   target remote | /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/../../bin/vgdb --pid=1649
==1649== --pid is optional if only one valgrind process is running
==1649== 
--1649-- REDIR: 0x100031a20 (dyld:strcmp) redirected to 0x25805c726 (???)
--1649-- REDIR: 0x10002bb0c (dyld:arc4random) redirected to 0x25805c7c4 (???)
--1649-- REDIR: 0x10002b9c0 (dyld:strlen) redirected to 0x25805c6f5 (???)
--1649-- REDIR: 0x10002b920 (dyld:strcpy) redirected to 0x25805c742 (???)
--1649-- REDIR: 0x10002f046 (dyld:strcat) redirected to 0x25805c706 (???)
--1649-- REDIR: 0x10002f084 (dyld:strlcat) redirected to 0x25805c75f (???)
--1649-- /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/vgpreload_core-amd64-darwin.so (rx at 0x1000a2000, rw at 0x1000a8000)
--1649--    reading syms   from primary file (3 88)
--1649--    dSYM= /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/vgpreload_core-amd64-darwin.so.dSYM/Contents/Resources/DWARF/vgpreload_core-amd64-darwin.so
--1649-- /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/vgpreload_memcheck-amd64-darwin.so (rx at 0x1000ac000, rw at 0x1000b5000)
--1649--    reading syms   from primary file (72 96)
--1649--    dSYM= /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/vgpreload_memcheck-amd64-darwin.so.dSYM/Contents/Resources/DWARF/vgpreload_memcheck-amd64-darwin.so
--1649-- /usr/lib/libc++.1.dylib (rx at 0x1000bb000, rw at 0x100112000)
--1649--    reading syms   from primary file (2023 1681)
--1649-- /usr/lib/libSystem.B.dylib (rx at 0x100172000, rw at 0x100174000)
--1649--    reading syms   from primary file (31 5)
--1649-- /usr/lib/libc++abi.dylib (rx at 0x10017a000, rw at 0x10019f000)
--1649--    reading syms   from primary file (369 212)
--1649-- /usr/lib/system/libcache.dylib (rx at 0x1001ae000, rw at 0x1001b3000)
--1649--    reading syms   from primary file (32 29)
--1649-- /usr/lib/system/libcommonCrypto.dylib (rx at 0x1001b8000, rw at 0x1001c3000)
--1649--    reading syms   from primary file (221 169)
--1649-- /usr/lib/system/libcompiler_rt.dylib (rx at 0x1001d0000, rw at 0x1001d8000)
--1649--    reading syms   from primary file (510 8)
--1649-- /usr/lib/system/libcopyfile.dylib (rx at 0x1001e5000, rw at 0x1001ee000)
--1649--    reading syms   from primary file (13 35)
--1649-- /usr/lib/system/libcorecrypto.dylib (rx at 0x1001f4000, rw at 0x100279000)
--1649--    reading syms   from primary file (511 669)
--1649-- /usr/lib/system/libdispatch.dylib (rx at 0x100295000, rw at 0x1002cf000)
--1649--    reading syms   from primary file (270 943)
--1649-- /usr/lib/system/libdyld.dylib (rx at 0x100309000, rw at 0x100327000)
--1649--    reading syms   from primary file (97 992)
--1649-- /usr/lib/system/libkeymgr.dylib (rx at 0x100341000, rw at 0x100342000)
--1649--    reading syms   from primary file (12 3)
--1649-- /usr/lib/system/libmacho.dylib (rx at 0x10034d000, rw at 0x100352000)
--1649--    reading syms   from primary file (105 1)
--1649-- /usr/lib/system/libquarantine.dylib (rx at 0x100358000, rw at 0x10035b000)
--1649--    reading syms   from primary file (67 32)
--1649-- /usr/lib/system/libremovefile.dylib (rx at 0x100361000, rw at 0x100363000)
--1649--    reading syms   from primary file (15 4)
--1649-- /usr/lib/system/libsystem_asl.dylib (rx at 0x100368000, rw at 0x100380000)
--1649--    reading syms   from primary file (222 225)
--1649-- /usr/lib/system/libsystem_blocks.dylib (rx at 0x10038d000, rw at 0x10038e000)
--1649--    reading syms   from primary file (21 6)
--1649-- /usr/lib/system/libsystem_c.dylib (rx at 0x100392000, rw at 0x10041c000)
--1649--    reading syms   from primary file (1340 804)
--1649-- /usr/lib/system/libsystem_configuration.dylib (rx at 0x100444000, rw at 0x100448000)
--1649--    reading syms   from primary file (38 66)
--1649-- /usr/lib/system/libsystem_coreservices.dylib (rx at 0x10044e000, rw at 0x100452000)
--1649--    reading syms   from primary file (14 37)
--1649-- /usr/lib/system/libsystem_darwin.dylib (rx at 0x100457000, rw at 0x100459000)
--1649--    reading syms   from primary file (12 105)
--1649-- /usr/lib/system/libsystem_dnssd.dylib (rx at 0x10045e000, rw at 0x100465000)
--1649--    reading syms   from primary file (49 24)
--1649-- /usr/lib/system/libsystem_info.dylib (rx at 0x10046b000, rw at 0x1004b5000)
--1649--    reading syms   from primary file (525 650)
--1649-- /usr/lib/system/libsystem_m.dylib (rx at 0x1004cc000, rw at 0x100518000)
--1649--    reading syms   from primary file (805 1)
--1649-- /usr/lib/system/libsystem_malloc.dylib (rx at 0x100526000, rw at 0x100546000)
--1649--    reading syms   from primary file (127 265)
--1649-- /usr/lib/system/libsystem_network.dylib (rx at 0x100552000, rw at 0x1005f6000)
--1649--    reading syms   from primary file (1097 1084)
--1649-- /usr/lib/system/libsystem_networkextension.dylib (rx at 0x10062f000, rw at 0x10063a000)
--1649--    reading syms   from primary file (96 229)
--1649-- /usr/lib/system/libsystem_notify.dylib (rx at 0x100646000, rw at 0x100650000)
--1649--    reading syms   from primary file (113 54)
--1649-- /usr/lib/system/libsystem_sandbox.dylib (rx at 0x100657000, rw at 0x10065b000)
--1649--    reading syms   from primary file (95 9)
--1649-- /usr/lib/system/libsystem_secinit.dylib (rx at 0x100661000, rw at 0x100663000)
--1649--    reading syms   from primary file (1 7)
--1649-- /usr/lib/system/libsystem_kernel.dylib (rx at 0x100668000, rw at 0x10068e000)
--1649--    reading syms   from primary file (1260 100)
--1649-- /usr/lib/system/libsystem_platform.dylib (rx at 0x1006a7000, rw at 0x1006af000)
--1649--    reading syms   from primary file (157 101)
--1649-- /usr/lib/system/libsystem_pthread.dylib (rx at 0x1006b7000, rw at 0x1006c3000)
--1649--    reading syms   from primary file (177 75)
--1649-- /usr/lib/system/libsystem_symptoms.dylib (rx at 0x1006cf000, rw at 0x1006d7000)
--1649--    reading syms   from primary file (10 93)
--1649-- /usr/lib/system/libsystem_trace.dylib (rx at 0x1006dd000, rw at 0x1006f1000)
--1649--    reading syms   from primary file (114 246)
--1649-- /usr/lib/system/libunwind.dylib (rx at 0x1006ff000, rw at 0x100705000)
--1649--    reading syms   from primary file (102 52)
--1649-- /usr/lib/system/libxpc.dylib (rx at 0x10070c000, rw at 0x100739000)
--1649--    reading syms   from primary file (565 901)
--1649-- /usr/lib/closure/libclosured.dylib (rx at 0x10075b000, rw at 0x10078f000)
--1649--    reading syms   from primary file (1 966)
--1649-- /usr/lib/libobjc.A.dylib (rx at 0x1007aa000, rw at 0x100b99000)
--1649--    reading syms   from primary file (369 902)
--1649-- REDIR: 0x1006a7ac0 (libsystem_platform.dylib:_platform_memchr$VARIANT$Haswell) redirected to 0x1000af4f6 (_platform_memchr$VARIANT$Haswell)
--1649-- REDIR: 0x1006a7ba0 (libsystem_platform.dylib:_platform_memcmp) redirected to 0x1000afa80 (_platform_memcmp)
--1649-- REDIR: 0x1006a80e0 (libsystem_platform.dylib:_platform_strncmp) redirected to 0x1000af3ec (_platform_strncmp)
--1649-- REDIR: 0x100393420 (libsystem_c.dylib:strlen) redirected to 0x1000af072 (strlen)
--1649-- REDIR: 0x1006a86a0 (libsystem_platform.dylib:_platform_strcmp) redirected to 0x1000af46d (_platform_strcmp)
--1649-- REDIR: 0x10052a5b8 (libsystem_malloc.dylib:calloc) redirected to 0x1000adf47 (calloc)
--1649-- REDIR: 0x100529c60 (libsystem_malloc.dylib:malloc_default_zone) redirected to 0x1000aec8d (malloc_default_zone)
--1649-- REDIR: 0x10052819a (libsystem_malloc.dylib:malloc_zone_malloc) redirected to 0x1000adb93 (malloc_zone_malloc)
--1649-- REDIR: 0x100529c69 (libsystem_malloc.dylib:malloc_zone_calloc) redirected to 0x1000ae135 (malloc_zone_calloc)
--1649-- REDIR: 0x1005274f3 (libsystem_malloc.dylib:malloc) redirected to 0x1000ad920 (malloc)
--1649-- REDIR: 0x100529d31 (libsystem_malloc.dylib:malloc_zone_from_ptr) redirected to 0x1000aecce (malloc_zone_from_ptr)
--1649-- REDIR: 0x10052965d (libsystem_malloc.dylib:free) redirected to 0x1000add09 (free)
--1649-- REDIR: 0x10052a76f (libsystem_malloc.dylib:realloc) redirected to 0x1000ae2c9 (realloc)
--1649-- REDIR: 0x1006a82c0 (libsystem_platform.dylib:_platform_strchr$VARIANT$Haswell) redirected to 0x1000aef3e (_platform_strchr$VARIANT$Haswell)
Hello, World!
==1649== 
==1649== HEAP SUMMARY:
==1649==     in use at exit: 22,368 bytes in 164 blocks
==1649==   total heap usage: 185 allocs, 21 frees, 30,816 bytes allocated
==1649== 
==1649== Searching for pointers to 164 not-freed blocks
==1649== Checked 10,808,072 bytes
==1649== 
==1649== 72 bytes in 3 blocks are possibly lost in loss record 26 of 43
==1649==    at 0x1000AE002: calloc (in /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/vgpreload_memcheck-amd64-darwin.so)
==1649==    by 0x1007AB7E2: map_images_nolock (in /usr/lib/libobjc.A.dylib)
==1649==    by 0x1007BE7DA: objc_object::sidetable_retainCount() (in /usr/lib/libobjc.A.dylib)
==1649==    by 0x100008C64: dyld::notifyBatchPartial(dyld_image_states, bool, char const* (*)(dyld_image_states, unsigned int, dyld_image_info const*), bool, bool) (in /usr/lib/dyld)
==1649==    by 0x100008E39: dyld::registerObjCNotifiers(void (*)(unsigned int, char const* const*, mach_header const* const*), void (*)(char const*, mach_header const*), void (*)(char const*, mach_header const*)) (in /usr/lib/dyld)
==1649==    by 0x10030C84D: _dyld_objc_notify_register (in /usr/lib/system/libdyld.dylib)
==1649==    by 0x1007AB075: _objc_init (in /usr/lib/libobjc.A.dylib)
==1649==    by 0x100296C04: _os_object_init (in /usr/lib/system/libdispatch.dylib)
==1649==    by 0x100296BEB: libdispatch_init (in /usr/lib/system/libdispatch.dylib)
==1649==    by 0x1001739C2: libSystem_initializer (in /usr/lib/libSystem.B.dylib)
==1649==    by 0x10001AA09: ImageLoaderMachO::doModInitFunctions(ImageLoader::LinkContext const&) (in /usr/lib/dyld)
==1649==    by 0x10001AC39: ImageLoaderMachO::doInitialization(ImageLoader::LinkContext const&) (in /usr/lib/dyld)
==1649== 
==1649== LEAK SUMMARY:
==1649==    definitely lost: 0 bytes in 0 blocks
==1649==    indirectly lost: 0 bytes in 0 blocks
==1649==      possibly lost: 72 bytes in 3 blocks
==1649==    still reachable: 4,296 bytes in 7 blocks
==1649==         suppressed: 18,000 bytes in 154 blocks
==1649== Reachable blocks (those to which a pointer was found) are not shown.
==1649== To see them, rerun with: --leak-check=full --show-leak-kinds=all
==1649== 
==1649== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 9 from 9)
--1649-- 
--1649-- used_suppression:      5 OSX1013:19-Leak /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:924 suppressed: 8,792 bytes in 5 blocks
--1649-- used_suppression:      7 OSX1013:17-Leak /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:906 suppressed: 3,744 bytes in 59 blocks
--1649-- used_suppression:      3 OSX1013:16-Leak /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:897 suppressed: 3,200 bytes in 50 blocks
--1649-- used_suppression:     16 OSX1013:10-Leak /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:839 suppressed: 2,144 bytes in 36 blocks
--1649-- used_suppression:      4 OSX1013:18-Leak /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:915 suppressed: 120 bytes in 4 blocks
--1649-- used_suppression:      1 OSX1013:dyld-3 /usr/local/Cellar/valgrind/HEAD-f19a956/lib/valgrind/default.supp:1267
==1649== 
==1649== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 9 from 9)
```

4)Анализ через OCLint:
```
$ oclint main.cpp -- -c
OCLint Report
Summary: TotalFiles=1 FilesWithViolations=0 P1=0 P2=0 P3=0 
[OCLint (http://oclint.org) v0.13]
```


