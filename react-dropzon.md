学习用react-Dropzone


1、用useState来存file及上传的setFile

2、定义创建一个可以拖拉拽上传的区域，还有上传的规格类型：



const {getRootProps, getInputProps} = useDropzone({   



//这里用useDropzone解构getRootProps（放置拖拉拽的区域）、getInputProps（处理拖拉拽的行为）

    accept: {
      'image/*': []
    },

//accept用来设定上传的image为什么格式，如果为[]的话则是可以接受所有格式，如果限制格式上传的话，如：“image/png, image/pdf”

    onDrop: acceptedFiles => {
      setFiles(acceptedFiles.map(file => Object.assign(file, {
        preview: URL.createObjectURL(file)
      })));
    }
  });

//这里的acceptedFiles指一个数组，包含了上传的；然后用setFiles来更新上传后的状态，用Object.assign来扩展上传的对象，添加preview的属性，然后preview则用 URL.createObjectURL这个来创建的，看看是file还是image，用于做预览的图片。


3、上传图片后的预览图：


const thumbs = files.map(file => (


//用map来循环files里的每个对象，就是上传后的files返回一个为JSX的预览图像，下面则可以自定义预览图像的样式


    <div style={thumb} key={file.name}>
      <div style={thumbInner}>
        <img
          src={file.preview}


//这里的src显示的就是上传后的file.preview的预览图，这里预览的url就是onDrop创建的；


          style={img}


//这里也可以用className来代替定义预览图的样式；

        
          onLoad={() => { URL.revokeObjectURL(file.preview) }}


//这里的onLoad为处理上传后的加载，图像加载完后就调用URL.revokeObjectURL(file.preview)然后释放出之前预览生成的内存；

        />
      </div>
    </div>
  ));


4、用useEffect来确保在组件卸载时释放分配给文件预览 URL 的内存，以避免内存泄漏：



useEffect(() => {
    return () => files.forEach(file) => URL.revokeObjectURL(file.preview));
  }, []);



//这里的依赖性为空，表示只会在组件卸载的时候执行一次

5、在组件中配置：


<section className="container"> 
    <div {...getRootProps({className: 'dropzone’})}>

        
//section为外层容器,这里配置getRootProps拖拉拽上传的区域


        <input {...getInputProps()} />

        
//这里配置的getInputProps（处理拖拉拽的行为）


        <p>Drag 'n' drop some files here, or click to select files</p> 
    </div> 
    <aside style={thumbsContainer}> 

    
//这里的aside用来展示上传的预览简缩图，可以通过className来设置不同的样式


     {thumbs} 
     </aside> 
</section>


//这里的thumbs就是通过map的方式生成的，如上列方法



