Detailed vulnerabilities information for the manuscript named "EM-Fuzz: Augmented Vulnerability Detection of EmbeddedFirmware with Practical Memory Checking" 

### 1. ICCP protocol application
#### 1) Bug-2019-0923
- Type: Segmentation fault (SIGSEGV)
- Description: An issue has been found in ICCP. It is a segmentation fault in acse.c.
- Call stack: 
```
SEGV on unknown address 0x000000000000 (pc 0x0000005da850 bp 0x000000000002 sp 0x7fd097afbd20 T4)          ==8829==The signal is caused by a READ memory access.                                                                                       ==8829==Hint: address points to the zero page.
    #0 0x5da84f in AcseConnection_parseMessage /root/libiec_iccp_mod/src/mms/iso_acse/acse.c:341
    #1 0x5980a0 in handleTcpConnection /root/libiec_iccp_mod/src/mms/iso_server/iso_connection.c:145
    #2 0x53a371 in destroyAutomaticThread /root/libiec_iccp_mod/src/hal/thread/linux/thread_linux.c:87
    #3 0x7fd09ca906b9 in start_thread (/lib/x86_64-linux-gnu/libpthread.so.0+0x76b9)
    #4 0x7fd09be9b41c in clone /build/glibc-LK5gWL/glibc-2.23/misc/../sysdeps/unix/sysv/linux/x86_64/clone.S:109

SEGV /root/libiec_iccp_mod/src/mms/iso_acse/acse.c:341 in AcseConnection_parseMessage
Thread T4 created by T1 here:
    #0 0x4327dd in __interceptor_pthread_create (/root/temp/iec/libiec_iccp_mod/examples/server_example1/server_example1+0x4327dd)
    #1 0x53a5e2 in Thread_start /root/libiec_iccp_mod/src/hal/thread/linux/thread_linux.c:98

Thread T1 created by T0 here:
    #0 0x4327dd in __interceptor_pthread_create (/root/temp/iec/libiec_iccp_mod/examples/server_example1/server_example1+0x4327dd)
    #1 0x53a5bd in Thread_start /root/libiec_iccp_mod/src/hal/thread/linux/thread_linux.c:102
```
#### 2) Bug-2019-0925
- Type: Heap buffer overflow
- Description: An issue has been found in ICCP. It is a heap-based buffer overflow in mms_client_example1.c.
- Call stack: 
```
heap-buffer-overflow on address 0x6280000040ff at pc 0x00000048e36f bp 0x7ffef31f51d0 sp 0x7ffef31f4980   WRITE of size 127 at 0x6280000040ff thread T0                                                                                                   #12 0x7fecd633e82f in __libc_start_main /build/glibc-LK5gWL/glibc-2.23/csu/../csu/libc-start.c:291
    #13 0x41a1c8 in _start (/root/temp/iec/libiec_iccp_mod/examples/mms_client_example1/mms_client_example1+0x41a1c8)

0x6280000040ff is located 1 bytes to the left of 16100-byte region [0x628000004100,0x628000007fe4)                                          allocated by thread T0 here:
    #0 0x4daee0 in calloc (/root/temp/iec/libiec_iccp_mod/examples/mms_client_example1/mms_client_example1+0x4daee0)
    #1 0x51443c in MmsConnection_create /root/libiec_iccp_mod/src/mms/iso_mms/client/mms_client_connection.c:790
```

#### 3) Bug-2019-0928
- Type: Heap buffer overflow
- Description: An issue has been found in ICCP. It is a heap-based buffer overflow in mms_client_example1.c.
- Call stack: 
```
heap-buffer-overflow on address 0x6280000040fd at pc 0x00000048e36f bp 0x7f
fe7f010010 sp 0x7ffe7f00f7c0   WRITE of size 223 at 0x6280000040fd thread T0 #0 0x48e36e in read (/root/temp/iec/libiec_iccp_mod/examples/mms_client_example1/mms_client_example1+0x48e36e)            #1 0x57b266 in read /usr/include/x86_64-linux-gnu/bits/unistd.h:44
    #2 0x57b266 in Socket_read /root/libiec_iccp_mod/src/hal/socket/linux/socket_linux.c:309
    #3 0x5e98cc in ByteStream_readOctets /root/libiec_iccp_mod/src/common/byte_stream.c:108
    #4 0x5a128d in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:577
    #5 0x5a128d in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #6 0x5a13df in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:590
    #7 0x5a13df in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #8 0x5a13df in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:590
    #9 0x5a13df in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #10 0x5a35df in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:590
    #11 0x5a35df in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #12 0x5a35df in CotpConnection_parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:650
    #13 0x522dac in IsoClientConnection_associate /root/libiec_iccp_mod/src/mms/iso_client/impl/iso_client_connection.c:382
    #14 0x514885 in MmsConnection_connect /root/libiec_iccp_mod/src/mms/iso_mms/client/mms_client_connection.c:887
    #15 0x5113e4 in main /root/temp/iec/libiec_iccp_mod/examples/mms_client_example1/mms_client_example1.c:38:6
    #16 0x7f9d34dc982f in __libc_start_main /build/glibc-LK5gWL/glibc-2.23/csu/../csu/libc-start.c:291
    #17 0x41a1c8 in _start (/root/temp/iec/libiec_iccp_mod/examples/mms_client_example1/mms_client_example1+0x41a1c8)
```
#### 4) Bug-2019-1003
- Type: Heap buffer overflow
- Description: An issue has been found in ICCP. It is a heap-based buffer overflow in client_example1.c.
- Call stack: 
```
heap-buffer-overflow on address 0x6280000040ff at pc 0x00000048e8df bp 0x7ffffed8b350 sp 0x7ffffed8ab00    WRITE of size 13 at 0x6280000040ff thread T0                                                                                                  #0 0x48e8de in read (/root/temp/iec/libiec_iccp_mod/examples/iec61850_client_example1/client_example1+0x48e8de)
    #1 0x61d236 in read /usr/include/x86_64-linux-gnu/bits/unistd.h:44
    #2 0x61d236 in Socket_read /root/libiec_iccp_mod/src/hal/socket/linux/socket_linux.c:309
    #3 0x681f3c in ByteStream_readOctets /root/libiec_iccp_mod/src/common/byte_stream.c:108
    #4 0x62ccdd in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:577
    #5 0x62ccdd in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #6 0x62f02f in addPayloadToBuffer /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:590
    #7 0x62f02f in parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:630
    #8 0x62f02f in CotpConnection_parseIncomingMessage /root/libiec_iccp_mod/src/mms/iso_cotp/cotp.c:650
    #9 0x5bfae5 in IsoClientConnection_associate /root/libiec_iccp_mod/src/mms/iso_client/impl/iso_client_connection.c:328
    #10 0x5b1805 in MmsConnection_connect /root/libiec_iccp_mod/src/mms/iso_mms/client/mms_client_connection.c:887
    #11 0x53c6ba in IedConnection_connect /root/libiec_iccp_mod/src/iedclient/impl/ied_connection.c:472
    #12 0x511c51 in main /root/temp/iec/libiec_iccp_mod/examples/iec61850_client_example1/client_example1.c:49:5
    #13 0x7f0fafea182f in __libc_start_main /build/glibc-LK5gWL/glibc-2.23/csu/../csu/libc-start.c:291
    #14 0x41a738 in _start (/root/temp/iec/libiec_iccp_mod/examples/iec61850_client_example1/client_example1+0x41a738)
```
### 2. IEC104 protocol application
#### 1) Bug-2019-0912
- Type: Heap buffer overflow
- Description: An issue has been found in IEC104. It is a heap-based buffer overflow in IEC10X/Iec104.c.
- Call stack: 
```    
 #0 0x40ab51 in Iec104_Deal_I ..//IEC10X/Iec104.c:1175
 #1 0x40b1cc in Iex104_Receive ..//IEC10X/Iec104.c:1305
 #2 0x410277 in Iec104_main /home/song/Downloads/IEC104/test/main.c:142
 #3 0x7ffff6a306b9 in start_thread (/lib/x86_64-linux-gnu/libpthread.so.0+0x76b9)
 #4 0x7ffff676641c in clone (/lib/x86_64-linux-gnu/libc.so.6+0x10741c)
```
#### 2) Bug-2019-0915
- Type: Stack buffer overflow
- Description: An issue has been found in IEC104. It is a stack-based buffer overflow in Iex104_Receive in IEC10X/Iec104.c.
- Call stack: 
```
stack-buffer-overflow on address 0x7fe592dfee6c at pc 0x00000040967c bp 0x7fe592dfe6c0 sp 0x7fe592dfe6b0
READ of size 1 at 0x7fe592dfee6c thread T1
    #0 0x40967b in Iex104_Receive ..//IEC10X/Iec104.c:1297
    #1 0x40b661 in Iec104_main /home/fouzhe/IEC104/test/main.c:140
    #2 0x7fe595f666b9 in start_thread (/lib/x86_64-linux-gnu/libpthread.so.0+0x76b9)
    #3 0x7fe595c9c41c in clone (/lib/x86_64-linux-gnu/libc.so.6+0x10741c)

Address 0x7fe592dfee6c is located in stack of thread T1 at offset 1852 in frame
    #0 0x40b12a in Iec104_main /home/fouzhe/IEC104/test/main.c:73

  This frame has 6 object(s):
    [32, 36) 'sin_size'
    [96, 100) 'on'
    [160, 168) 'tid1'
    [224, 240) 's_add'
    [288, 304) 'c_add'
    [352, 1852) 'Iec104_RecvBuf' <== Memory access at offset 1852 overflows this variable
HINT: this may be a false positive if your program uses some custom stack unwind mechanism or swapcontext
      (longjmp and C++ exceptions *are* supported)
Thread T1 created by T0 here:
    #0 0x7fe5963d6253 in pthread_create (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x36253)
    #1 0x40c190 in main /home/fouzhe/IEC104/test/main.c:301
    #2 0x7fe595bb582f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
```
#### 3) Bug-2019-0918
- Type: Segmentation fault (SIGSEGV)
- Description: An issue has been found in IEC104. It is a segmentation fault in Iex104_Deal_I in IEC10X/Iec104.c.
- Call stack: 
```
[DumpHEX]Length:6 
68:04:43:00:02:21
Send Ok!
hC!IEC10X_Enqueue,Prio(0) elementNum(0)len(6)(6) 
Tester Count(2)... 
Thread 2 "iec104_monitor" received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7ffff37ff700 (LWP 42308)]
0x0000000000000000 in ?? ()
(gdb) backtrace
#0  0x0000000000000000 in ?? ()
#1  0x000000000040a605 in Iec104_Deal_I (Iec104Data=Iec104Data@entry=0x7ffff37fe880, len=len@entry=137) at ../IEC10X/Iec104.c:1214
#2  0x000000000040adac in Iex104_Receive (buf=buf@entry=0x7ffff37fe880 "h\207", len=len@entry=8) at ../IEC10X/Iec104.c:1305
#3  0x000000000040fe67 in Iec104_main (arg=<optimized out>) at main.c:138
#4  0x00007ffff6a306ba in start_thread (arg=0x7ffff37ff700) at pthread_create.c:333
#5  0x00007ffff676641d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109
```
#### 4) Bug-2019-0921
- Type: Segmentation fault (SIGSEGV)
- Description: An issue has been found in IEC104. It is a segmentation fault in Iec104_Deal_FirmUpdate in IEC10X/Iec104.c.
- Call stack: 
```
SEGV on unknown address 0x000000000000 (pc 0x000000000000 bp 0x000000000001 sp 0x7f21286fe4e8 T1
"#0  0x0000000000000000 in ?? ()
#1  0x0000000000409999 in Iec104_Deal_FirmUpdate (asdu=asdu@entry=0x7ffff37fe886, Len=Len@entry=0x6a) at ..//IEC10X/Iec104.c:1066
#2  0x000000000040a9c9 in Iec104_Deal_I (Iec104Data=Iec104Data@entry=0x7ffff37fe880, len=len@entry=0x6a) at ..//IEC10X/Iec104.c:1208
#3  0x000000000040b1cd in Iex104_Receive (buf=buf@entry=0x7ffff37fe880 ""hhhhh"", len=len@entry=0x5dc) at ..//IEC10X/Iec104.c:1305
#4  0x0000000000410278 in Iec104_main (arg=<optimized out>) at main.c:142
#5  0x00007ffff6a306ba in start_thread (arg=0x7ffff37ff700) at pthread_create.c:333
#6  0x00007ffff676641d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109"										
```
### 3. IEC61850 protocol application
#### 1) CVE-2018-18834
- Type: Heap buff overflow
- Description: An issue has been found in IEC61850. It is a heap-based buffer overflow in BerEncoder_encodeOctetString in mms/asn1/ber_encoder.c.
- Call stack:
```
heap-buffer-overflow on address 0x61b00001f76e at pc 0x0000004174d3 bp 0x7ffc577e1890 sp 0x7ffc577e1880
WRITE of size 1 at 0x61b00001f76e thread T0
    #0 0x4174d2 in BerEncoder_encodeOctetString src/mms/asn1/ber_encoder.c:122
    #1 0x41be56 in MmsValue_encodeMmsData src/mms/iso_mms/server/mms_access_result.c:384
    #2 0x412dd3 in createGoosePayload src/goose/goose_publisher.c:347
    #3 0x412ea4 in GoosePublisher_publish src/goose/goose_publisher.c:362
    #4 0x40223b in main /home/fouzhe/documents/libiec61850/examples/goose_publisher/goose_publisher_example.c:132
    #5 0x7f58fe16b82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #6 0x4017a8 in _start (/home/fouzhe/documents/libiec61850/examples/goose_publisher/goose_publisher_example+0x4017a8)

0x61b00001f76e is located 0 bytes to the right of 1518-byte region [0x61b00001f180,0x61b00001f76e)
allocated by thread T0 here:
    #0 0x7f58fe7ca602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x414612 in Memory_malloc hal/memory/lib_memory.c:47
    #2 0x411ff8 in prepareGooseBuffer src/goose/goose_publisher.c:197
    #3 0x411795 in GoosePublisher_create src/goose/goose_publisher.c:72
    #4 0x4021bf in main /home/fouzhe/documents/libiec61850/examples/goose_publisher/goose_publisher_example.c:121
    #5 0x7f58fe16b82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
```
#### 2) CVE-2018-18937
- Type: NULL pointer dereference
- Description: An issue has been found in libIEC61850 v1.3. It is a NULL pointer dereference in ClientDataSet_getValues in client/ied_connection.c.
- Call stack: 
```
SEGV on unknown address 0x000000000008 (pc 0x000000412330 bp 0x7ffedff5df40 sp 0x7ffedff5df30 T0)
    #0 0x41232f in ClientDataSet_getValues src/iec61850/client/ied_connection.c:216
    #1 0x402a06 in main /home/fouzhe/libiec61850_pure/libiec61850/examples/iec61850_client_example4/client_example4.c:77
    #2 0x7f8f5eb6682f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #3 0x402658 in _start (/home/fouzhe/libiec61850_pure/libiec61850/examples/iec61850_client_example4/client_example4+0x402658)
```

#### 3) CVE-2018-19093
- Type: Segmentation fault (SIGSEGV)
- Description: An issue has been found in libIEC61850 v1.3. It is a SEGV in ControlObjectClient_setCommandTerminationHandler in client/client_control.c. NOTE: the software maintainer disputes this because it requires incorrect usage of the client_example_control program.
- Call stack: 
```
SEGV on unknown address 0x000000000050 (pc 0x00000044a3d4 bp 0x60800000bfa0 sp 0x7ffd097d60c0 T0)
    #0 0x44a3d3 in ControlObjectClient_setCommandTerminationHandler src/iec61850/client/client_control.c:267
    #1 0x405af2 in main /home/fouzhe/my_fuzz/libiec61850/examples/iec61850_client_example_control/client_example_control.c:191
    #2 0x7f557490f82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #3 0x4093b8 in _start (/home/fouzhe/my_fuzz/libiec61850/examples/iec61850_client_example_control/client_example_control+0x4093b8)
```
#### 4) CVE-2018-19121
- Type: Segmentation fault (SIGSEGV)
- Description: 	An issue has been found in libIEC61850 v1.3. It is a SEGV in Ethernet_receivePacket in ethernet_bsd.c.
- Call stack: 
```
SEGV on unknown address 0x00000010 (pc 0x0008b013 bp 0xb078ce68 sp 0xb078cd50 T1)
==76989==The signal is caused by a READ memory access.
==76989==Hint: address points to the zero page.
    #0 0x8b012 in Ethernet_receivePacket ethernet_bsd.c:369
    #1 0x83b2f in SVReceiver_tick sv_subscriber.c:547
    #2 0x8342d in svReceiverLoop sv_subscriber.c:167
    #3 0x8880b in destroyAutomaticThread thread_bsd.c:88
    #4 0x17d185 in __asan::AsanThread::ThreadStart(unsigned long, __sanitizer::atomic_uintptr_t*) (libclang_rt.asan_osx_dynamic.dylib:i386+0x5f185)
    #5 0x16a039 in asan_thread_start(void*) (libclang_rt.asan_osx_dynamic.dylib:i386+0x4c039)
    #6 0xa1754046 in _pthread_body (libsystem_pthread.dylib:i386+0x4046)
    #7 0xa1753f8e in _pthread_start (libsystem_pthread.dylib:i386+0x3f8e)
    #8 0xa1753849 in thread_start (libsystem_pthread.dylib:i386+0x3849)

==76989==Register values:
eax = 0x00000010  ebx = 0x001ff800  ecx = 0x20000002  edx = 0x00000000
edi = 0x018f4000  esi = 0x00000000  ebp = 0xb078ce68  esp = 0xb078cd50
Thread T1 created by T0 here:
    #0 0x169ed3 in wrap_pthread_create (libclang_rt.asan_osx_dynamic.dylib:i386+0x4bed3)
    #1 0x885ea in Thread_start thread_bsd.c:99
    #2 0x8331e in SVReceiver_start sv_subscriber.c:186
    #3 0x7eda9 in main sv_subscriber_example.c:76
    #4 0xa1541394 in start (libdyld.dylib:i386+0x5394)

```
#### 5) CVE-2018-19122
- Type: NULL pointer dereference
- Description: An issue has been found in libIEC61850 v1.3. It is a NULL pointer dereference in Ethernet_sendPacket in ethernet_bsd.c.
- Call stack: 
```
SEGV on unknown address 0x00000000 (pc 0x0004e3bd bp 0xbffe6a18 sp 0xbffe69e0 T0)
==77056==The signal is caused by a READ memory access.
==77056==Hint: address points to the zero page.
    #0 0x4e3bc in Ethernet_sendPacket ethernet_bsd.c:416
    #1 0x4500c in SVPublisher_publish sv_publisher.c:488
    #2 0x1acc7 in main sv_publisher_example.c:70
    #3 0xa1541394 in start (libdyld.dylib:i386+0x5394)

==77056==Register values:
eax = 0x00000000  ebx = 0x00000000  ecx = 0x20000000  edx = 0x00000000
edi = 0x00000000  esi = 0x02f03880  ebp = 0xbffe6a18  esp = 0xbffe69e0
```
#### 6) CVE-2018-19185
- Type: Heap buffer overflow
- Description: An issue has been found in libIEC61850 v1.3. It is a heap-based buffer overflow in BerEncoder_encodeOctetString in mms/asn1/ber_encoder.c. This is exploitable even after CVE-2018-18834 has been patched, with a different dataSetValue sequence than the CVE-2018-18834 attack vector.
- Call stack: 
```
heap-buffer-overflow on address 0x61b00001f76e at pc 0x00000045624c bp 0x7fff45a10840 sp 0x7fff45a10830
WRITE of size 1 at 0x61b00001f76e thread T0
    #0 0x45624b in BerEncoder_encodeOctetString src/mms/asn1/ber_encoder.c:122
    #1 0x4477f3 in createGoosePayload src/goose/goose_publisher.c:347
    #2 0x4477f3 in GoosePublisher_publish src/goose/goose_publisher.c:362
    #3 0x402baf in main /home/fouzhe/my_fuzz/libiec61850/examples/goose_publisher/goose_publisher_example.c:253
    #4 0x7fc57f71782f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #5 0x4032c8 in _start (/home/fouzhe/my_fuzz/libiec61850/examples/goose_publisher/goose_publisher_example+0x4032c8)

0x61b00001f76e is located 0 bytes to the right of 1518-byte region [0x61b00001f180,0x61b00001f76e)
allocated by thread T0 here:
    #0 0x7fc57fd76602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x44b610 in Memory_malloc hal/memory/lib_memory.c:47
```
#### 7) CVE-2019-6136
- Type: Segmentation fault (SIGSEGV)
- Description: An issue has been found in libIEC61850 v1.3.1. Ethernet_setProtocolFilter in hal/ethernet/linux/ethernet_linux.c has a SEGV, as demonstrated by sv_subscriber_example.c and sv_subscriber.c.
- Call stack: 
```
SEGV on unknown address 0x00000000000a (pc 0x55b5675c1284 bp 0x7f92623fee30 sp 0x7f92623fee20 T1)
==1403==The signal is caused by a WRITE memory access.
==1403==Hint: address points to the zero page.
    #0 0x55b5675c1283 in Ethernet_setProtocolFilter /home/input0/Desktop/libiec61850/hal/ethernet/linux/ethernet_linux.c:209
    #1 0x55b5675ba75f in SVReceiver_startThreadless /home/input0/Desktop/libiec61850/src/sampled_values/sv_subscriber.c:232
    #2 0x55b5675ba3b7 in svReceiverLoop /home/input0/Desktop/libiec61850/src/sampled_values/sv_subscriber.c:163
    #3 0x55b5675c1720 in destroyAutomaticThread /home/input0/Desktop/libiec61850/hal/thread/linux/thread_linux.c:90
    #4 0x7f9265c976da in start_thread (/lib/x86_64-linux-gnu/libpthread.so.0+0x76da)
    #5 0x7f92659c088e in __clone (/lib/x86_64-linux-gnu/libc.so.6+0x12188e)
/home/input0/Desktop/libiec61850/hal/ethernet/linux/ethernet_linux.c:209 in Ethernet_setProtocolFilter
Thread T1 created by T0 here:
    #0 0x7f9265ee6d2f in __interceptor_pthread_create (/usr/lib/x86_64-linux-gnu/libasan.so.4+0x37d2f)
    #1 0x55b5675c17ab in Thread_start /home/input0/Desktop/libiec61850/hal/thread/linux/thread_linux.c:101
    #2 0x55b5675ba49a in SVReceiver_start /home/input0/Desktop/libiec61850/src/sampled_values/sv_subscriber.c:186
    #3 0x55b5675b9eec in main /home/input0/Desktop/libiec61850/examples/sv_subscriber/sv_subscriber_example.c:76
    #4 0x7f92658c0b96 in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x21b96)
```
### 4. OpenSSL toolkit
#### 1) CVE-2016-2108
- Type:  Denial of Service
- Description: The ASN.1 implementation in OpenSSL before 1.0.1o and 1.0.2 before 1.0.2c allows remote attackers to execute arbitrary code or cause a denial of service (buffer underflow and memory corruption) via an ANY field in crafted serialized data, aka the "negative zero" issue.
- Call stack: 
```
Error in `/usr/local/ssl/bin/openssl': free(): invalid next size (fast): 0x0000000001013010
#0  0x00007ffff7843c37 in __GI_raise (sig=sig@entry=6)
    at ../nptl/sysdeps/unix/sysv/linux/raise.c:56
#1  0x00007ffff7847028 in __GI_abort () at abort.c:89
#2  0x00007ffff78802a4 in __libc_message (do_abort=do_abort@entry=1, 
    fmt=fmt@entry=0x7ffff7992350 "*** Error in `%s': %s: 0x%s ***\n")
    at ../sysdeps/posix/libc_fatal.c:175
#3  0x00007ffff788c82e in malloc_printerr (ptr=<optimized out>, 
    str=0x7ffff79924f0 "free(): invalid next size (fast)", action=1) at malloc.c:4998
#4  _int_free (av=<optimized out>, p=<optimized out>, have_lock=0) at malloc.c:3842
#5  0x000000000049773d in CRYPTO_free ()
#6  0x00000000004fba6b in sk_pop_free ()
#7  0x0000000000531513 in ASN1_generate_v3 ()
#8  0x0000000000531c60 in ASN1_generate_nconf ()
#9  0x00000000004062a0 in asn1parse_main ()
#10 0x0000000000404a21 in do_cmd ()
#11 0x000000000040476f in main ()
```
#### 2) Bug-2018-1226
- Type: Stack overflow
- Description: An issue has been found in OpenSSL 1.0.2b. It is a stack-based buffer overflow in the OPENSSL_cpuid_setup function.
- Call stack: 
```
=> 0x00092028 <_armv7_tick+0>:	mrc	15, 0, r0, cr9, cr13, {0}
   0x0009202c <_armv7_tick+4>:	bx	lr
   0x00092030 <OPENSSL_atomic_add+0>:	ldrex	r2, [r0]
   0x00092034 <OPENSSL_atomic_add+4>:	add	r3, r2, r1
   0x00092038 <OPENSSL_atomic_add+8>:	strex	r2, r3, [r0]
   0x0009203c <OPENSSL_atomic_add+12>:	cmp	r2, #0
   0x00092040 <OPENSSL_atomic_add+16>:	bne	0x92030 <OPENSSL_atomic_add>
   0x00092044 <OPENSSL_atomic_add+20>:	mov	r0, r3
   0x00092048 <OPENSSL_atomic_add+24>:	bx	lr
   0x0009204c <OPENSSL_cleanse+0>:	eor	r12, r12, r12
   0x00092050 <OPENSSL_cleanse+4>:	cmp	r1, #7
   0x00092054 <OPENSSL_cleanse+8>:	subcs	r1, r1, #4
   0x00092058 <OPENSSL_cleanse+12>:	bcs	0x92074 <OPENSSL_cleanse+40>

#0  0x00092028 in _armv7_tick ()
#1  0x00013e48 in OPENSSL_cpuid_setup ()
#2  0x00196560 in __libc_csu_init ()
#3  0x76e6660c in __libc_start_main (main=0x7efff234, argc=1996009472, argv=0x76e6660c <__libc_start_main+168>, init=0x196514 <__libc_csu_init>,
    fini=0x196574 <__libc_csu_fini>, rtld_fini=0x76fdf2a4 <_dl_fini>, stack_end=0x7efff234) at libc-start.c:247
#4  0x00013ec8 in _start ()
Backtrace stopped: previous frame identical to this frame (corrupt stack?)
```
### 5. HTSlib library
#### 1) CVE-2018-13843
- Type: Memory leak
- Description: An issue has been found in HTSlib 1.8. It is a memory leak in bgzf_getline in bgzf.c. NOTE: the software maintainer's position is that the "failure to free memory" can be fixed in applications that use the HTSlib library (such as test/test_bgzf.c in the original report) and is not a library issue.
- Call stack: 
```
detected memory leaks

Direct leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f7e77d58961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x425d8e in bgzf_getline /home/mfc_fuzz/htslib/bgzf.c:1800
    #2 0x40b885 in test_bgzf_getline test/test_bgzf.c:691
    #3 0x40c72f in main test/test_bgzf.c:774
    #4 0x7f7e770ad82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Direct leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f7e77d58961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x425d8e in bgzf_getline /home/mfc_fuzz/htslib/bgzf.c:1800
    #2 0x40b885 in test_bgzf_getline test/test_bgzf.c:691
    #3 0x40c711 in main test/test_bgzf.c:773
    #4 0x7f7e770ad82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Direct leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f7e77d58961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x425d8e in bgzf_getline /home/mfc_fuzz/htslib/bgzf.c:1800
    #2 0x40b885 in test_bgzf_getline test/test_bgzf.c:691
    #3 0x40c74d in main test/test_bgzf.c:775
    #4 0x7f7e770ad82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
```
#### 2) CVE-2018-13844
- Type: Memory leak
- Description: An issue has been found in HTSlib 1.8. It is a memory leak in fai_read in faidx.c.
- Call stack: 
```
detected memory leaks

Direct leak of 40 byte(s) in 1 object(s) allocated from:
    #0 0x7f829603879a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x40cb6b in fai_read /home/mfc_fuzz/htslib/faidx.c:358
    #2 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #3 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #4 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #5 0x4040e7 in main test/test_realn.c:75
    #6 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 131072 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x5d523e in bgzf_read_init /home/mfc_fuzz/htslib/bgzf.c:222
    #2 0x5d6717 in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:309
    #3 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 128 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x40a18a in fai_insert_index /home/mfc_fuzz/htslib/faidx.c:86
    #2 0x40cfd2 in fai_read /home/mfc_fuzz/htslib/faidx.c:400
    #3 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 104 byte(s) in 1 object(s) allocated from:
    #0 0x7f829603879a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x5d519c in bgzf_read_init /home/mfc_fuzz/htslib/bgzf.c:218
    #2 0x5d6717 in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:309
    #3 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 64 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x413cd7 in hfile_init /home/mfc_fuzz/htslib/hfile.c:98
    #2 0x4195d8 in hopen_fd /home/mfc_fuzz/htslib/hfile.c:608
    #3 0x41ffbc in hopen /home/mfc_fuzz/htslib/hfile.c:1041
    #4 0x5d66bb in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:308
    #5 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #6 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #7 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #8 0x4040e7 in main test/test_realn.c:75
    #9 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 64 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x407199 in kh_resize_s /home/mfc_fuzz/htslib/faidx.c:51
    #2 0x408cd6 in kh_put_s /home/mfc_fuzz/htslib/faidx.c:51
    #3 0x409df0 in fai_insert_index /home/mfc_fuzz/htslib/faidx.c:74
    #4 0x40cfd2 in fai_read /home/mfc_fuzz/htslib/faidx.c:400
    #5 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #6 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #7 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #8 0x4040e7 in main test/test_realn.c:75
    #9 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 54 byte(s) in 6 object(s) allocated from:
    #0 0x7f829600230f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x409d66 in fai_insert_index /home/mfc_fuzz/htslib/faidx.c:72
    #2 0x40cfd2 in fai_read /home/mfc_fuzz/htslib/faidx.c:400
    #3 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 40 byte(s) in 1 object(s) allocated from:
    #0 0x7f829603879a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x406522 in kh_init_s /home/mfc_fuzz/htslib/faidx.c:51
    #2 0x40cbc4 in fai_read /home/mfc_fuzz/htslib/faidx.c:361
    #3 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 40 byte(s) in 1 object(s) allocated from:
    #0 0x7f829603879a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x5d0c3e in kh_init_cache /home/mfc_fuzz/htslib/bgzf.c:80
    #2 0x5d5653 in bgzf_read_init /home/mfc_fuzz/htslib/bgzf.c:232
    #3 0x5d6717 in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:309
    #4 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #5 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #6 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #7 0x4040e7 in main test/test_realn.c:75
    #8 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x5d5513 in bgzf_read_init /home/mfc_fuzz/htslib/bgzf.c:228
    #2 0x5d6717 in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:309
    #3 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #4 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #5 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #6 0x4040e7 in main test/test_realn.c:75
    #7 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 4 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x407009 in kh_resize_s /home/mfc_fuzz/htslib/faidx.c:51
    #2 0x408cd6 in kh_put_s /home/mfc_fuzz/htslib/faidx.c:51
    #3 0x409df0 in fai_insert_index /home/mfc_fuzz/htslib/faidx.c:74
    #4 0x40cfd2 in fai_read /home/mfc_fuzz/htslib/faidx.c:400
    #5 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #6 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #7 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #8 0x4040e7 in main test/test_realn.c:75
    #9 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
```
#### 3) CVE-2018-13945
- Type: Memory leak
- Description: An issue has been found in HTSlib 1.8. It is a memory leak in hfile.c.
- Call stack: 
```
detected memory leaks
Indirect leak of 4096 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x413d29 in hfile_init /home/mfc_fuzz/htslib/hfile.c:105
    #2 0x4195d8 in hopen_fd /home/mfc_fuzz/htslib/hfile.c:608
    #3 0x41ffbc in hopen /home/mfc_fuzz/htslib/hfile.c:1041
    #4 0x5d66bb in bgzf_open /home/mfc_fuzz/htslib/bgzf.c:308
    #5 0x40f0df in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:640
    #6 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #7 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #8 0x4040e7 in main test/test_realn.c:75
    #9 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

Indirect leak of 256 byte(s) in 1 object(s) allocated from:
    #0 0x7f8296038961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x407281 in kh_resize_s /home/mfc_fuzz/htslib/faidx.c:51
    #2 0x408cd6 in kh_put_s /home/mfc_fuzz/htslib/faidx.c:51
    #3 0x409df0 in fai_insert_index /home/mfc_fuzz/htslib/faidx.c:74
    #4 0x40cfd2 in fai_read /home/mfc_fuzz/htslib/faidx.c:400
    #5 0x40ef67 in fai_load3_core /home/mfc_fuzz/htslib/faidx.c:627
    #6 0x40f53f in fai_load3 /home/mfc_fuzz/htslib/faidx.c:667
    #7 0x40f5a2 in fai_load /home/mfc_fuzz/htslib/faidx.c:673
    #8 0x4040e7 in main test/test_realn.c:75
    #9 0x7f829508482f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
```

### 6. MXML utilities
#### 1) CVE-2018-20004
- Type: Stack overflow
- Description: An issue has been found in Mini-XML (aka mxml) 2.12. It is a stack-based buffer overflow in mxml_write_node in mxml-file.c via vectors involving a double-precision floating point number and the `<order type="real">` substring, as demonstrated by testmxml.
- Call stack: 
```
stack-buffer-overflow on address 0x7ffe99d748ff at pc 0x00000049147b bp 0x7ffe99d746e0 sp 0x7ffe99d73e90
WRITE of size 269 at 0x7ffe99d748ff thread T0
    #0 0x49147a in __interceptor_vsprintf /home/fouzhe/llvm/llvm/projects/compiler-rt/lib/asan/../sanitizer_common/sanitizer_common_interceptors.inc:1572
    #1 0x4915d2 in __interceptor_sprintf /home/fouzhe/llvm/llvm/projects/compiler-rt/lib/asan/../sanitizer_common/sanitizer_common_interceptors.inc:1615
    #2 0x53c97c in mxml_write_node /home/fouzhe/my_fuzz/mxml/mxml-file.c:2914:4
    #3 0x53c97c in mxmlSaveFile /home/fouzhe/my_fuzz/mxml/mxml-file.c:339
    #4 0x518e98 in main /home/fouzhe/my_fuzz/mxml/testmxml.c:568:3
    #5 0x7f4e00bb282f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #6 0x41a178 in _start (/home/fouzhe/my_fuzz/mxml/testmxml+0x41a178)

Address 0x7ffe99d748ff is located in stack of thread T0 at offset 287 in frame
    #0 0x53b88f in mxmlSaveFile /home/fouzhe/my_fuzz/mxml/mxml-file.c:329

  This frame has 1 object(s):
    [32, 287) 's.i' (line 2727) <== Memory access at offset 287 overflows this variable

```
#### 2) CVE-2018-20005
- Type: Use after free
- Description: An issue has been found in Mini-XML (aka mxml) 2.12. It is a use-after-free in mxmlWalkNext in mxml-search.c, as demonstrated by mxmldoc.
- Call stack: 
```
heap-use-after-free on address 0x608000008ec0 at pc 0x7fedf0751729 bp 0x7fff65264ee0 sp 0x7fff65264ed0
READ of size 8 at 0x608000008ec0 thread T0
    #0 0x7fedf0751728 in mxmlWalkNext /home/fouzhe/my_fuzz/mxml/mxml-search.c:212
    #1 0x7fedf075180c in mxmlFindElement /home/fouzhe/my_fuzz/mxml/mxml-search.c:101
    #2 0x405074 in sort_node /home/fouzhe/my_fuzz/mxml/mxmldoc.c:3372
    #3 0x405b5d in scan_file /home/fouzhe/my_fuzz/mxml/mxmldoc.c:1981
    #4 0x402b1d in main /home/fouzhe/my_fuzz/mxml/mxmldoc.c:503
    #5 0x7fedeff5d82f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #6 0x402ff8 in _start (/home/fouzhe/my_fuzz/mxml/mxmldoc+0x402ff8)

0x608000008ec0 is located 32 bytes inside of 88-byte region [0x608000008ea0,0x608000008ef8)
freed by thread T0 here:
    #0 0x7fedf09f92ca in __interceptor_free (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x982ca)
    #1 0x4050c1 in sort_node /home/fouzhe/my_fuzz/mxml/mxmldoc.c:3389

previously allocated by thread T0 here:
    #0 0x7fedf09f979a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x7fedf0750e50 in mxml_new /home/fouzhe/my_fuzz/mxml/mxml-node.c:844
```
#### 3) CVE-2018-19764
- Type: Memory leak
- Description: An issue has been found in Mini-XML (aka mxml) 2.12. It is a memory leak in mxml/mxml-node.c.
- Call stack: 
```
Indirect leak of 5984 byte(s) in 68 object(s) allocated from:
    #0 0x7f28b77de79a in __interceptor_calloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x9879a)
    #1 0x4196be in mxml_new /home/fouzhe/my_fuzz/mxml/mxml-node.c:844

Indirect leak of 215 byte(s) in 25 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x4197fc in mxmlNewElement /home/fouzhe/my_fuzz/mxml/mxml-node.c:386

Indirect leak of 112 byte(s) in 7 object(s) allocated from:
    #0 0x7f28b77de602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x41422c in mxml_set_attr /home/fouzhe/my_fuzz/mxml/mxml-attr.c:322

Indirect leak of 99 byte(s) in 9 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x41472b in mxmlElementSetAttr /home/fouzhe/my_fuzz/mxml/mxml-attr.c:224

Indirect leak of 56 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x62635f797469746d  (<unknown module>)

Indirect leak of 54 byte(s) in 2 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x706972637365641f  (<unknown module>)

Indirect leak of 50 byte(s) in 9 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x4142b2 in mxml_set_attr /home/fouzhe/my_fuzz/mxml/mxml-attr.c:337

Indirect leak of 34 byte(s) in 17 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574

Indirect leak of 32 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77de961 in realloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98961)
    #1 0x414240 in mxml_set_attr /home/fouzhe/my_fuzz/mxml/mxml-attr.c:324

Indirect leak of 30 byte(s) in 6 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x745f62635f6373  (<unknown module>)

Indirect leak of 27 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455

Indirect leak of 24 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x756c61762065646e  (<unknown module>)

Indirect leak of 23 byte(s) in 3 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x726f74706971ff  (<unknown module>)

Indirect leak of 17 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x7265666675622071  (<unknown module>)

Indirect leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x656d616e207973  (<unknown module>)

Indirect leak of 16 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419882 in mxmlNewOpaque /home/fouzhe/my_fuzz/mxml/mxml-node.c:455
    #2 0x726f7470697262  (<unknown module>)

Indirect leak of 14 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x7400735f667561  (<unknown module>)

Indirect leak of 11 byte(s) in 2 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x62635f79746973  (<unknown module>)

Indirect leak of 11 byte(s) in 2 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x6b0a2e2e2e74726e  (<unknown module>)

Indirect leak of 5 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x6e6f697469736f6f  (<unknown module>)

Indirect leak of 4 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x7463757274732063  (<unknown module>)

Indirect leak of 4 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0x62635f797469746d  (<unknown module>)

Indirect leak of 4 byte(s) in 1 object(s) allocated from:
    #0 0x7f28b77a830f in strdup (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x6230f)
    #1 0x419af3 in mxmlNewText /home/fouzhe/my_fuzz/mxml/mxml-node.c:574
    #2 0xa2e2e2e74726e  (<unknown module>)
```
