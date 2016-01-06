# java-.dbf-
java读取dbf解决Failed to parse Number: For input string: "-.---"错误
最近要做一个程序，数据源是DBF的文件，我用Java解析它，maven导入
<dependency>
    <groupId>com.linuxense</groupId>
    <artifactId>javadbf</artifactId>
    <version>0.4.0</version>
</dependency>
这个是最新的，读取从某公司获取的数据出现Failed to parse Number: For input string: "-.---" ，经过调试把里面DBFReader类里面的：
