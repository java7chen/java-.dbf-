# java-.dbf-
java读取dbf解决Failed to parse Number: For input string: "-.---"错误
最近要做一个程序，数据源是DBF的文件，我用Java解析它，maven导入
<dependency>
    <groupId>com.linuxense</groupId>
    <artifactId>javadbf</artifactId>
    <version>0.4.0</version>
</dependency>
这个是最新的，读取从某公司获取的数据出现Failed to parse Number: For input string: "-.---" ，
（注：以下来源于网络）
经过调试把里面DBFReader类里面的：
case 'N':
     try {
           byte t_numeric[] = new byte[ this.header.fieldArray[i].getFieldLength()];
           dataInputStream.read( t_numeric);
           t_numeric = Utils.trimLeftSpaces( t_numeric);
           String strtemp = new String( t_numeric);
           if(strtemp.equals("-.---") || strtemp.equals("-")){
              recordObjects[i]=0.0;//这行代码，在你只需要输出里面的数据时，可以不用加，不会出错。当你要读用这里面的数据时就必须加。
                continue;
            }//这里是我自己加上的代码，就是屏蔽这个错误的。
由于CSDN下载需要积分，自己打包了一个，可以解决目前java读取DBF出现的错误。
