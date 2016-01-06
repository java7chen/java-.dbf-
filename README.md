# Java解析DBF文件
java读取dbf解决Failed to parse Number: For input string: "-.---"错误,最近要做一个程序，数据源是DBF的文件，我用Java解析它，maven导入
<br/>&lt;dependency>
  <br/>&lt;groupId>com.linuxense&lt;/groupId>
   <br/>&lt;artifactId>javadbf&lt;/artifactId>
  <br/> &lt;version>0.4.0&lt;/version>
<br/>&lt;/dependency>
<br/>这个是最新的，读取从某公司获取的数据出现Failed to parse Number: For input string: "-.---" ，
（注：以下来源于网络）
经过调试把里面DBFReader类里面的：
<br/>case 'N':
     <br/>try {
           <br/>byte t_numeric[] = new byte[ this.header.fieldArray[i].getFieldLength()];
          <br/> dataInputStream.read( t_numeric);
          <br/> t_numeric = Utils.trimLeftSpaces( t_numeric);
          <br/> String strtemp = new String( t_numeric);
          <br/> if(strtemp.equals("-.---") || strtemp.equals("-")){
           <br/>   recordObjects[i]=0.0;//这行代码，在你只需要输出里面的数据时，可以不用加，不会出错。当你要读用这里面的数据时就必须加。
               <br/> continue;
         <br/>   }//这里是我自己加上的代码，就是屏蔽这个错误的。
<br/>由于CSDN下载需要积分，自己打包了一个，可以解决目前java读取DBF出现的错误。
