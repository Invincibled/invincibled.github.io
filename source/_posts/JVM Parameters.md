---
title: JVM Parameters
date: 2020-8-10
updated: 2020-8-10
---



推荐内容:

http://jvmmemory.com/

https://docs.oracle.com/javase/8/docs/technotes/tools/unix/java.html#BABDJJFI



# JVM  Paramters

**声明：本文基于JDK1.8所做说明**

JVM参数 共分为三种：

* 标准参数（-），所有的JVM实现都必须实现这些参数的功能，而且向后兼容，例如(java --help)
* 非标准参数（-X），默认jvm实现这些参数的功能，但是并不保证所有jvm实现都满足，且不保证向后兼容，例如（java -X)
* 非Stable参数（-XX），此类参数各个jvm实现会有所不同，这些都是不稳定的并且不推荐在生产环境中使用。将来可能会随时取消，需要慎重使用；上都被实现），而且如果在新版本有什么改动也不会发布通知。
  对响应时间要求很高的系统来说，良好掌握JVM关于GC调优的参数是很重要的。比如一个高流量地延迟的电子交易平台，他要求的响应时间都是毫秒级的。要获得适合的参数组合需要大量的分析和不断的尝试，更依赖于交易系统的特性。

关于JVM选项的几点：

1. 布尔型参数选项：-XX:+ 打开， -XX:- 关闭。（比如-XX:+PrintGCDetails）

2. 数字型参数选项通过-XX:=设定。数字可以是m/M(兆字节)，k/K(千字节)，g/G(G字节)。
   比如：32K表示32768字节。（比如-XX:HeapDumpPath=./java_pid.hprof）

3. 字符行参数选项通过-XX:=设定，通常用来指定一个文件，路径，或者一个命令列表。（比如-XX:+PrintGCDetails）如果你想查看当前应用使用的JVM参数，你可以使用：ManagementFactory.getRuntimeMXBean().getInputArguments()。

   

##  Standard Options



| Option and Default Value                         | Description |
| ------------------------------------------------ | ----------- |
| -agentlib:*libname*[=*options*]                  |             |
| -agentpath:pathname[=options]                    |             |
| -client                                          |             |
| -Dproperty***=***value                           |             |
| -d32                                             |             |
| -d64                                             |             |
| -disableassertions[:[packagename]...[:classname] |             |
| -da[:[packagename]...[:classname]                |             |
| -disablesystemassertions                         |             |
| -dsa                                             |             |
| -enableassertions[:[packagename]...[:classname]  |             |
| -ea[:[packagename]...[:classname]                |             |
| -enablesystemassertions                          |             |
| -esa                                             |             |
| -help                                            |             |
| -jar filename                                    |             |
| -javaagent:jarpath[=options]                     |             |
| -jre-restrict-search                             |             |
| -no-jre-restrict-search                          |             |
| -server                                          |             |
| -showversion                                     |             |
| -splash:imgname                                  |             |
| -verbose:class                                   |             |
| -verbose:gc                                      |             |
| -verbose:jni                                     |             |
| -version                                         |             |
| -version:release                                 |             |

## Non-Standard Options



| Option and Default Value | Description |
| ------------------------ | ----------- |
| -X                       |             |
| -Xbatch                  |             |
| -Xbootclasspath:path     |             |
| -Xbootclasspath/a:path   |             |
| -Xbootclasspath/p:path   |             |
| -Xcheck:jni              |             |
| -Xcomp                   |             |
| -Xdebug                  |             |
| -Xdiag                   |             |
| -Xfuture                 |             |
| -Xint                    |             |
| -Xinternalversion        |             |
| -Xloggc:filename         |             |
| -Xmaxjitcodesize=size    |             |
| -Xmixed                  |             |
| -Xmnsize                 |             |
| -Xmssize                 |             |
| -Xmxsize                 |             |
| -Xnoclassgc              |             |
| -Xprof                   |             |
| -Xrs                     |             |
| -Xshare:mode             |             |
| -XshowSettings:category  |             |
| -Xsssize                 |             |
| -Xusealtsigs             |             |
| -Xverify:mode            |             |

## Advanced Runtime Options



| Option and Default Value                                 | Description |
| -------------------------------------------------------- | ----------- |
| -XX:+CheckEndorsedAndExtDirs                             |             |
| -XX:+DisableAttachMechanism                              |             |
| -XX:ErrorFile=filename                                   |             |
| -XX:+FailOverToOldVerifier                               |             |
| -XX:+FlightRecorder                                      |             |
| -XX:-FlightRecorder                                      |             |
| -XX:FlightRecorderOptions=*parameter*=value              |             |
| -XX:LargePageSizeInBytes=size                            |             |
| -XX:MaxDirectMemorySize=size                             |             |
| -XX:NativeMemoryTracking=mode                            |             |
| -XX:ObjectAlignmentInBytes=alignment                     |             |
| -XX:OnError=string                                       |             |
| -XX:OnOutOfMemoryError=string                            |             |
| -XX:+PerfDataSaveToFile                                  |             |
| -XX:-PreferContainerQuotaForCPUCount                     |             |
| -XX:+PrintCommandLineFlags                               |             |
| -XX:+PrintContainerInfo                                  |             |
| -XX:+PrintNMTStatistics                                  |             |
| -XX:+RelaxAccessControlCheck                             |             |
| -XX:+ResourceManagement                                  |             |
| -XX:ResourceManagementSampleInterval=value(milliseconds) |             |
| -XX:SharedArchiveFile=path                               |             |
| -XX:SharedClassListFile=file_name                        |             |
| -XX:+ShowMessageBoxOnError                               |             |
| -XX:StartFlightRecording=parameter=value                 |             |
| -XX:ThreadStackSize=size                                 |             |
| -XX:+TraceClassLoading                                   |             |
| -XX:+TraceClassLoadingPreorder                           |             |
| -XX:+TraceClassResolution                                |             |
| -XX:+TraceClassUnloading                                 |             |
| -XX:+TraceLoaderConstraints                              |             |
| -XX:+UnlockCommercialFeatures                            |             |
| -XX:+UseAltSigs                                          |             |
| -XX:+UseAppCDS                                           |             |
| -XX:-UseBiasedLocking                                    |             |
| -XX:-UseCompressedOops                                   |             |
| -XX:-UseContainerSupport                                 |             |
| -XX:+UseHugeTLBFS                                        |             |
| -XX:+UseLargePages                                       |             |
| -XX:+UseMembar                                           |             |
| -XX:+UsePerfData                                         |             |
| -XX:+UseTransparentHugePages                             |             |
| -XX:+AllowUserSignalHandlers                             |             |

## Advanced JIT Compiler Options



| Option and Default Value                   | Descritpion |
| ------------------------------------------ | ----------- |
| -XX:+AggressiveOpts                        |             |
| -XX:AllocateInstancePrefetchLines=*lines*  |             |
| -XX:AllocatePrefetchDistance=size          |             |
| -XX:AllocatePrefetchInstr=instruction      |             |
| -XX:AllocatePrefetchLines=lines            |             |
| -XX:AllocatePrefetchStepSize=size          |             |
| -XX:AllocatePrefetchStyle=style            |             |
| -XX:+BackgroundCompilation                 |             |
| -XX:CICompilerCount=threads                |             |
| -XX:CodeCacheMinimumFreeSpace=size         |             |
| -XX:CompileCommand=command,method[,option] |             |
| -XX:CompileCommandFile=filename            |             |
| -XX:CompileOnly=methods                    |             |
| -XX:CompileThreshold=invocations           |             |
| -XX:+DoEscapeAnalysis                      |             |
| -XX:InitialCodeCacheSize=size              |             |
| -XX:+Inline                                |             |
| -XX:InlineSmallCode=size                   |             |
| -XX:+LogCompilation                        |             |
| -XX:MaxInlineSize=size                     |             |
| -XX:MaxNodeLimit=nodes                     |             |
| -XX:MaxTrivialSize=size                    |             |
| -XX:+OptimizeStringConcat                  |             |
| -XX:+PrintAssembly                         |             |
| -XX:+PrintCompilation                      |             |
| -XX:+PrintInlining                         |             |
| -XX:ReservedCodeCacheSize=size             |             |
| -XX:RTMAbortRatio=abort_ratio              |             |
| -XX:RTMRetryCount=number_of_retries        |             |
| -XX:-TieredCompilation                     |             |
| -XX:+UseAES                                |             |
| -XX:+UseAESIntrinsics                      |             |
| -XX:+UseCodeCacheFlushing                  |             |
| -XX:+UseCondCardMark                       |             |
| -XX:+UseRTMDeopt                           |             |
| -XX:+UseRTMLocking                         |             |
| -XX:+UseSHA                                |             |
| -XX:+UseSHA1Intrinsics                     |             |
| -XX:+UseSHA256Intrinsics                   |             |
| -XX:+UseSHA512Intrinsics                   |             |
| -XX:+UseSuperWord                          |             |

## Advanced Serviceability Options



| Option and Default Value        | Description |
| ------------------------------- | ----------- |
| -XX:+ExtendedDTraceProbes       |             |
| -XX:+HeapDumpOnOutOfMemoryError |             |
| -XX:HeapDumpPath=path           |             |
| -XX:LogFile=path                |             |
| -XX:+PrintClassHistogram        |             |
| -XX:+PrintConcurrentLocks       |             |
| -XX:+UnlockDiagnosticVMOptions  |             |

## Advanced Garbage Collection Options



| Option and Default Value                          | Description |
| ------------------------------------------------- | ----------- |
| -XX:ActiveProcessorCount=x                        |             |
| -XX:+AggressiveHeap                               |             |
| -XX:+AlwaysPreTouch                               |             |
| -XX:+CMSClassUnloadingEnabled                     |             |
| -XX:CMSExpAvgFactor=percent                       |             |
| -XX:CMSInitiatingOccupancyFraction=percent        |             |
| -XX:+CMSScavengeBeforeRemark                      |             |
| -XX:CMSTriggerRatio=percent                       |             |
| -XX:ConcGCThreads=threads                         |             |
| -XX:+DisableExplicitGC                            |             |
| -XX:+ExplicitGCInvokesConcurrent                  |             |
| -XX:+ExplicitGCInvokesConcurrentAndUnloadsClasses |             |
| -XX:G1HeapRegionSize=size                         |             |
| -XX:+G1PrintHeapRegions                           |             |
| -XX:G1ReservePercent=percent                      |             |
| -XX:InitialHeapSize=size                          |             |
| -XX:InitialRAMPercentage=percent                  |             |
| -XX:InitialSurvivorRatio=ratio                    |             |
| -XX:InitiatingHeapOccupancyPercent=percent        |             |
| -XX:MaxGCPauseMillis=time                         |             |
| -XX:MaxHeapSize=size                              |             |
| -XX:MaxHeapFreeRatio=percent                      |             |
| -XX:MaxMetaspaceSize=size                         |             |
| -XX:MaxNewSize=size                               |             |
| -XX:MaxRAMPercentage=percent                      |             |
| -XX:MaxTenuringThreshold=threshold                |             |
| -XX:MetaspaceSize=size                            |             |
| -XX:MinHeapFreeRatio=percent                      |             |
| -XX:MinRAMPercentage=percent                      |             |
| -XX:NewRatio=ratio                                |             |
| -XX:NewSize=size                                  |             |
| -XX:ParallelGCThreads=threads                     |             |
| -XX:+ParallelRefProcEnabled                       |             |
| -XX:+PrintAdaptiveSizePolicy                      |             |
| -XX:+PrintGC                                      |             |
| -XX:+PrintGCApplicationConcurrentTime             |             |
| -XX:+PrintGCApplicationStoppedTime                |             |
| -XX:+PrintGCDateStamps                            |             |
| -XX:+PrintGCDetails                               |             |
| -XX:+PrintGCTaskTimeStamps                        |             |
| -XX:+PrintGCTimeStamps                            |             |
| -XX:+PrintStringDeduplicationStatistics           |             |
| -XX:+PrintTenuringDistribution                    |             |
| -XX:+ScavengeBeforeFullGC                         |             |
| -XX:SoftRefLRUPolicyMSPerMB=time                  |             |
| -XX:StringDeduplicationAgeThreshold=threshold     |             |
| -XX:SurvivorRatio=ratio                           |             |
| -XX:TargetSurvivorRatio=percent                   |             |
| -XX:TLABSize=size                                 |             |
| -XX:+UseAdaptiveSizePolicy                        |             |
| -XX:+UseCMSInitiatingOccupancyOnly                |             |
| -XX:+UseConcMarkSweepGC                           |             |
| -XX:+UseG1GC                                      |             |
| -XX:+UseGCOverheadLimit                           |             |
| -XX:+UseNUMA                                      |             |
| -XX:+UseParallelGC                                |             |
| -XX:+UseParallelOldGC                             |             |
| -XX:+UseParNewGC                                  |             |
| -XX:+UseSerialGC                                  |             |
| -XX:+UseSHM                                       |             |
| -XX:+UseStringDeduplication                       |             |
| -XX:+UseTLAB                                      |             |



## Deprecated and Removed Options



| -Xincgc                                        |      |
| ---------------------------------------------- | ---- |
| -Xrunlibname                                   |      |
| -XX:CMSIncrementalDutyCycle=percent            |      |
| -XX:CMSIncrementalDutyCycleMin=percent         |      |
| -XX:+CMSIncrementalMode                        |      |
| -XX:CMSIncrementalOffset=percent               |      |
| -XX:+CMSIncrementalPacing                      |      |
| -XX:CMSIncrementalSafetyFactor=percent         |      |
| -XX:CMSInitiatingPermOccupancyFraction=percent |      |
| -XX:MaxPermSize=size                           |      |
| -XX:PermSize=size                              |      |
| -XX:+UseSplitVerifier                          |      |
| -XX:+UseStringCache                            |      |

随时更新