# js-file-upload-demo
js/web  文件上传完整demo
 
> **如有帮助谢谢star**   :star::star::star::star::star: 
 
 
 - 效果预览图：
 
 <img src="show/1.jpg" >
 
 
 - 简要教程
 
ssi-uploader是一款带预览图并且可以拖拽文件的jQuery ajax文件上传插件。该文件上传插件支持AJAX，支持多文件上传，可控制上的文件格式和文件大小，提供各种回调函数，使用非常方便。


 - 使用方法
 
在页面中引入ssi-uploader.css和ssi-uploader.js文件。
 
> <link rel="stylesheet" href="path/to/ssi-uploader.css">

> <script src="path/to/ssi-uploader.js"></script>  


 - HTML结构

最基本的文件上传HTML结构是使用一个<input>元素，类型为file，并指定一个id。

> <input type="file" multiple id="ssi-upload"/>

 -  初始化插件

在页面DOM元素加载完毕之后，可以通过ssi_uploader方法来初始化该文件上传插件。

> $('#ssi-upload').ssi_uploader({
    url: 'path/to/upload.php'
});   

 -  配置参数
 
 ssi_uploader文件上传插件的可用配置参数如下：
 
<table>
    <thead>
      <tr>
        <td>参数</td>
        <td>类型</td>
        <td>默认值</td>
        <td>描述</td>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>url</td>
        <td>{String}</td>
        <td>null</td>
        <td>接收ajax请求的地址。必须填写。</td>
      </tr>
      <tr>
        <td>data</td>
        <td>{Object}</td>
        <td>null</td>
        <td>发送请求的额外数据。例如<code>$('input').ssi-uploader({url:'upload.php',data:{"name":"myDragon"}})</code></td>
      </tr>
      <tr>
        <td>ajaxOptions</td>
        <td>{Object}</td>
        <td>{type:'DELETE'}</td>
        <td>扩展默认的<code>$.ajax</code>函数的选项。</td>
      </tr>
      <tr>
        <td>locale</td>
        <td>{String}</td>
        <td>"en"</td>
        <td>使用的本地化语言。</td>
      </tr>
      <tr>
        <td>preview</td>
        <td>{boolean}</td>
        <td>true</td>
        <td>是否启用文件预览图效果。</td>
      </tr>
      <tr>
        <td>maxNumberOfFiles</td>
        <td>{Number}</td>
        <td>null</td>
        <td>每次允许上传多少个文件。</td>
      </tr>
      <tr>
        <td>maxFileSize</td>
        <td>{Number}</td>
        <td>null</td>
        <td>允许上传的最大文件尺寸。</td>
      </tr>
      <tr>
        <td>allowed</td>
        <td>{Array}</td>
        <td>['jpg', 'jpeg', 'png', 'bmp', 'gif']</td>
        <td>允许上传的文件类型。</td>
      </tr>
      <tr>
        <td>errorHandler</td>
        <td>{Object}</td>
        <td></td>
        <td>用于处理错误信息的方法。</td>
      </tr>
      <tr>
        <td>beforeUpload</td>
        <td>{Function}</td>
        <td></td>
        <td>文件上传前执行的回调函数。</td>
      </tr>
      <tr>
        <td>beforeEachUpload</td>
        <td>{Function}</td>
        <td></td>
        <td>每一个单独的文件上传前执行的回调函数。</td>
      </tr>
      <tr>
        <td>onUpload</td>
        <td>{Function}</td>
        <td></td>
        <td>文件上传后执行的回调函数。</td>
      </tr>
      <tr>
        <td>onEachUpload</td>
        <td>{Function}</td>
        <td></td>
        <td>每一个单独的文件上传后执行的回调函数。</td>
      </tr>
      <tr>
        <td>responseValidation</td>
        <td>{Object||false}</td>
        <td></td>
        <td>设置错误校验，插件将显示设置的信息。可以可以是：<code>{ type:"error",result:"Already exists" }</code>或<code>{ error:"Already exists." }</code>。</td>
      </tr>
    </tbody>
  </table>
  
其中，errorHandler参数带有一个errorHandler.method函数，该函数错误信息和类型。
  
 > function(msg,type){alert(msg);}  
  
responseValidation对象的可用属性有：

> validationKey：类型{String||Object}，设置验证信息。

> resultKey：类型{String||Object}，设置返回验证信息。

> success：类型{String}，设置成功信息。

> error：类型{String}，设置错误信息。

例如：


//structure 1
$('#ss-uploader').ssi_uploader({
  responseValidation:{
    validationKey: 'type',
    resultKey: 'data',
    success: 'success',
    error: 'error'
  }
});
 
//result
 /*
  {
    type:'error',
    data:'Already Exists.'
  } 
*/
 
//structure 2
$('#ss-uploader').ssi_uploader({
  responseValidation:{
    validationKey: {
      success: 'success',
      error: 'error'
    },
    resultKey: 'validationKey'
  }
})
//result
 /*
  {
    error:'Already Exists.'
  } 
*/





