# 简介

## 日志工具

### Android日志工具Log

+ Android的日志工具为`Log`（android.util.log）
+ 一下五个方法用来打印日志：（级别从低打高）
    >方法|级别|打印信息
    >|:-|:--|:------|
    >Log.v()|verbose|最琐碎、意义最小的日志信息
    >Log.d()|debug|调试信息
    >Log.i()|info|一些比较重要、可以用于分析用户行为的信息
    >Log.w()|warn|警告信息
    >Log.e()|error|错误信息
+ 不使用System.out打印信息的原因：
    1. 日志打印不可控
    2. 打印时间无法确定
    3. 不能添加过滤器
    4. 日志没有级别区分
