### apply、call的实现
参考链接：https://github.com/mqyqingfeng/Blog/issues/11
* call的实现
    Function.prototype.myCall = function(context) {
        //考虑绑定对象为null的情况
        var context = Object(context) || window;

        //将函数设置为对象的属性
        context.fn = this;

        //参数
        var args = [];
        for(var i = 1, len = arguments.length; i < len; i++){
            args.push('arguments[' + i + ']');
        }
        console.log(args);

        //执行该函数
        var result = eval('context.fn(' + args + ')');

        //删除该函数
        delete context.fn;
        return result;
    }

    var testObj = {
        value: 1
    };
    function testFunc(name, age){
        console.log(name);
        console.log(age);
        console.log(this.value);
    }
    testFunc.myCall(testObj, 'yxq', 18);
* apply的实现
    Function.prototype.myApply = function(context, arr){
        //考虑绑定对象为null的情况
        var context = Object(context) || window;

        //将函数设置为对象的属性
        context.fn = this;

        //参数
        var result,
            args = [];
        //执行该函数
        if (arr) {
            for (var i = 0, len = arr.length; i < len; i++) {
                args.push('arr[' + i + ']');
            }
            result = eval('context.fn(' + args + ')');
        } else {
            result = context.fn();
        }

        //删除该函数
        delete context.fn;
        return result;
    }
### 文件下载
参考网站：StackOverFlow
    function downloadExcel(xhRequest, header, fileName){
        var xhr = new XMLHttpRequest();
        xhr.open(xhRequest.type, xhRequest.url);
        xhr.setRequestHeader('token', header.token);
        xhr.responseType = 'blob';
        xhr.onload = function(){
            if (xhr.status === 200) {
                var ele = document.createElement('a');
                document.body.appendChild(ele);
                ele.style.cssText = 'display:none';
                var blob = new Blob([this.response], {type: 'application/vnd.ms-excel'});
                if (navigator.appVersion.toString().indexOf('.net') > 0) {
                    window.navigator.msSaveBlob(blob, fileName);
                } else {
                    var windowUrl = window.URL || window.webkitURL || {},
                        url = windowUrl.createObjectURL(blob);
                    ele.href = url;
                    ele.download = fileName;
                    ele.click();
                    setTimeout(function(){
                        document.body.removeChild(ele);
                        windowUrl.revokeObjectURL(url);
                    }, 0);
                }
            } else {
                console.log(xhr.status);
            }
        }
    }

