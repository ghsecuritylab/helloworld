# FILE 模块说明

__FILE__

<div class="bi-table">
  <table>
    <colgroup>
      <col width="90px" />
      <col width="90px" />
      <col width="90px" />
    </colgroup>
    <tbody>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">API</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">参数说明</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">使用注意</div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">FILE.issupport()</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">功能： 查询是否支持FILE文件系统操作接口。</div>
          <div data-type="p"></div>
          <div data-type="p">参数：无</div>
          <div data-type="p"></div>
          <div data-type="p">返回值：1，支持</div>
          <div data-type="p">0，不支持</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">在使用FILE文件操作前，建议先使用FILE.issupport操作，对于嵌入式操作系统，某些可能不支持该接口。</div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">FILE.read(filepath)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">功能：读取文件内容</div>
          <div data-type="p"></div>
          <div data-type="p">参数：文件完整路径</div>
          <div data-type="p"></div>
          <div data-type="p">返回值：读取失败返回空字符串，读取成功返回读取的文件内容</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">FILE.delete(filepath)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">功能：删除文件</div>
          <div data-type="p"></div>
          <div data-type="p">参数：文件完整路径</div>
          <div data-type="p"></div>
          <div data-type="p">返回值：0 删除成功</div>
          <div data-type="p">其他 删除文件失败</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">FILE.write(filepath,buffer,mode)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">功能：往指定文件写入指定buffer的内容。</div>
          <div data-type="p"></div>
          <div data-type="p">参数：filepath 文件路径</div>
          <div data-type="p">buffer 待写入的文件缓冲区。</div>
          <div data-type="p">mode 写入的文件模式。</div>
          <div data-type="p"></div>
          <div data-type="p">返回值：0写文件成功</div>
          <div data-type="p">其他，写文件失败</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">mode可以为</div>
          <div data-type="p">&quot;w&quot;,&quot;r&quot;,&quot;w+&quot;,&quot;r+&quot;,&quot;a&quot;,&quot;a+&quot;</div>
          <div data-type="p">类似与fopen(const char * restrict path, const char * restrict mode)的参数mode。</div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p">FILE.rename(filepath)</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p">功能：重命名一个文件</div>
          <div data-type="p">参数：文件路径</div>
          <div data-type="p">返回值： 0 操作成功</div>
          <div data-type="p">其他，操作失败。</div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
      </tr>
      <tr>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
        <td rowspan="1" colSpan="1">
          <div data-type="p"></div>
        </td>
      </tr>
    </tbody>
  </table>
</div>


js测试程序示例：

```
var fsenable = FS.issupport();
console.log('FS enable '+fsenable);
var writefile = 'test FS write buffer:hello world';
var ret = FS.write('/spiffs/hello.js',writefile,'w+');
console.log('FS.write+'+ret);
var ret = FS.read('/spiffs/hello.js');
console.log('FS read hello.js ='+ ret);
var ret = FS.rename('/spiffs/hello.js','/spiffs/hello1.js');
console.log('FS rename ='+ ret);
var ret = FS.read('/spiffs/hello1.js');
console.log('FS read hello1.js='+ ret);
var ret = FS.delete('/spiffs/hello1.js');
console.log('FS delete ='+ ret);
```

示例运行log如下：

```
BoneEngine > FS enable 1 
FS.write(/spiffs/hello.js,test FS write buffer:hello world,w+);
BoneEngine > FS.write+0 
BoneEngine > FS read hello.js =test FS write buffer:hello world 
BoneEngine > FS rename =0 
BoneEngine > FS read hello1.js=test FS write buffer:hello world 
BoneEngine > FS delete =0 
```

 