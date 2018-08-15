bootstrap-fileinput
===================

[![Bower version](https://badge.fury.io/bo/bootstrap-fileinput.svg)](http://badge.fury.io/bo/bootstrap-fileinput)
[![Latest Stable Version](https://poser.pugx.org/kartik-v/bootstrap-fileinput/v/stable)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![License](https://poser.pugx.org/kartik-v/bootstrap-fileinput/license)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![Packagist Downloads](https://poser.pugx.org/kartik-v/bootstrap-fileinput/downloads)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![Monthly Downloads](https://poser.pugx.org/kartik-v/bootstrap-fileinput/d/monthly)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)

An enhanced HTML 5 file input for Bootstrap 3.x and 4.x with file preview for various files, offers multiple selection, and more. The plugin allows you a simple way to setup an advanced file picker/upload control built to work specially with Bootstrap CSS3 styles. It enhances the file input functionality further, by offering support to preview a wide variety of files i.e. images, text, html, video, audio, flash, and objects. In addition, it includes AJAX based uploads, dragging &amp; dropping files, viewing upload progress, and selectively previewing, adding, or deleting files.

![Krajee Default Theme](https://lh3.googleusercontent.com/8m5BKa-o2_W63OuL-NJtAYOxelboHccfsDojxdqhmVCxY49LTiSVK8rOywzup2EDJlXcda_SsKkMVA=w1366-h768-rw-no)

> NOTE: An alternative new [Krajee Explorer Theme](http://plugins.krajee.com/file-krajee-explorer-demo) (preview shown below) for `bootstrap-fileinput` has been released and available since v4.3.7. For more theming options and suggestions refer the [theming demos](http://plugins.krajee.com/file-theme-demo).

![Krajee Explorer Theme](https://lh3.googleusercontent.com/eKMw_la1h6Z0y1Vk0SU3fsWVpmUoqg_HS-ZEZ1U2-1e8s6fgFZqoGbXcRjIXbYLkLi6Ns17-nb2yOg=w1366-h768-rw-no)

js
$(".file-input").fileinput({
    language: 'zh',
    uploadUrl: '/upload/uploadify', //上传后台操作的方法
    showPreview: false,
    showUpload: false,
    uploadExtraData: {},
    uploadAsync: false,
    allowedFileExtensions: ['jpg', 'gif', 'png'],//接收的文件后缀
    maxFileCount: 1, //允许同时上传的最大文件个数
    autoReplace: true,
    previewFileType: 'video', //预览文件类型,内置['image', 'html', 'text', 'video', 'audio', 'flash', 'object','other']
    browseLabel: '',
    browseClass: 'btn btn-primary btn-icon',
    browseIcon: '<i class="icon-plus22"></i> ',
    removeLabel: '',
    uploadLabel: '',
    initialPreviewAsData: true,
    uploadClass: 'btn btn-default btn-icon',
    uploadIcon: '<i class="icon-file-upload"></i> ',
    removeClass: 'btn btn-danger btn-icon',
    removeIcon: '<i class="icon-cancel-square"></i> ',
    layoutTemplates: {
        caption: '<div tabindex="-1" class="form-control file-caption {class}">\n' + '<span class="icon-file-plus kv-caption-icon" style="display: inline"></span><input style="margin:-20px 0 0 20px" class="file-caption-name"/>\n' + '</div>'
    }
}).on("fileclear",function (event, data, msg) {
}).on("filebatchselected",function (event, files) { //选择文件自动上传
    $(this).fileinput("upload");
}).on('fileuploaded',function (event, data, previewId, index) { //成功后回调
    var form = data.form, files = data.files, extra = data.extra,
        response = data.response, reader = data.reader;
}).on('fileuploaderror',function (event, data, msg) {
    var form = data.form, files = data.files, extra = data.extra,
        response = data.response, reader = data.reader;
    // get message
    alert(msg);
}).on('filebatchuploaderror', function (event, data, msg) {
    var form = data.form, files = data.files, extra = data.extra,
        response = data.response, reader = data.reader;
    // get message
    alert(msg);
});

public function actionUploadify() {
    //echo json_encode(['error'=>'An error exception message if applicable']);die;
    $result['initialPreview'] = [
        "<img src='/images/desert.jpg' class='file-preview-image' alt='Desert' title='Desert'>"
    ];
    $result['initialPreviewConfig'] = [
        'caption' => 'desert.jpg',
        'width' => '120px',
        'url' => 'http://localhost/avatar/delete',
        'key' => 100,
        'extra' => ['id' => 100],
    ];
    $result['initialPreviewThumbTags'] = [
        'caption' => '',
        'width' => "<span class='custom-css'>CUSTOM MARKUP</span>",
    ];
    $result['append'] = true;
    echo json_encode($result);
}
