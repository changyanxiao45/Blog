# input file css reset
通过为label元素声明一个for属性，并将for属性指向一个隐藏的input元素即可实现。(label的for属性必须匹配file元素的ID)
	<label for="file-upload" class="custom-file-upload">
	    Custom Upload
	</label>
	<input id="file-upload" type="file"/>

另外  还可以这样实现

	<label class="custom-file-upload">
	    <input type="file"/>
	    Custom Upload
	</label>

隐藏input元素

	input[type="file"] {
	    display: none;
	}

由于IE8及以下版本不支持以上的方式，同时，jQuery默认不会去验证隐藏的元素，考虑到以上两个原因，你可以通过其他的方式去隐藏input元素。

	input[type="file"] {
	    position: absolute;
	    width: 1px;
	    height: 1px;
	    padding: 0;
	    margin: -1px;
	    overflow: hidden;
	    clip: rect(0,0,0,0);
	    border: 0;
	}

	input[type="file"] {
	    position: fixed;
	    right: 100%;
	    bottom: 100%;
	}

最后，重写label的样式。

	.custom-file-upload {
	    border: 1px solid #ccc;
	    display: inline-block;
	    padding: 6px 12px;
	    cursor: pointer;
	}
	
