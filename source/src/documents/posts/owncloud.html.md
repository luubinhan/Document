---
layout: 'content'
title: 'OwnCloud'
description: 'Your Cloud, Your Data, Your Way!'
---

#### Table of Content
-------------

<!-- MarkdownTOC depth=2 -->

- Install
- Theming
- Chèn thêm js và css
- Bật debug mode
- Thêm kích thước file trên trang download
- Thêm share link trên trang download
- Thêm ngày expiration trên trang download
- Confirm trước khi delete
- Tự động share file khi upload
- Thêm share link trên trang list file
- Chèn giá trị vào khi load cùng với icon
- Tuỳ biến khi gởi email

<!-- /MarkdownTOC -->

## Install 

* Download source file: [owncloud.org](http://owncloud.org/)
* Upload to localhost
* Run and follow setup step

![Image](http://i0.wp.com/imagecdn5.maketecheasier.com/2012/01/owncloud-first-run-wizard.png?resize=600%2C365)

View this [Article](http://www.maketecheasier.com/install-and-configure-owncloud/2012/01/11)


## Theming

[Document](http://owncloud.org/theming/)

* Place your theme in the theme folder <code>/themes</code>.
* Activate by putting <code>'theme' => ‘themename’</code>, into the <code>/config/config.php</code> file



## Chèn thêm js và css

Xem [bài viết hướng dẫn](http://creadicted.com/snippets/including-custom-librarys-insinde-of-owncloud/)

## Bật debug mode

Debug mode sẽ không nén file js, css

Mở file **config/config.php** thêm dòng sau vào cuối

```php
define( "DEBUG", 1);
```

## Thêm kích thước file trên trang download

Thông tin này mặc định không trả về ở giao diện trang download file, mở file **Apps/Files_Sharing/public.php** thêm dòng

```php
$tmpl->assign('size', \OC\Files\Filesystem::filesize($file)); 
```

vào phía dưới đoạn code <code>$tmpl->assign('filename', $file);</code>

Trên trang **Apps/Files_Sharing/Templates/public.php**

```php
p($_['size']);
```

Hiển thị kích thước file đã format

```php
p(OCP\human_file_size($file['size']));
```

## Thêm share link trên trang download

Mở file **Apps/Files_Sharing/public.php** thêm dòng

```php
$tmpl->assign('linkShare', OCP\Util::linkToPublic('files') . $urlLinkIdentifiers); 
```

Trên trang **Apps/Files_Sharing/Templates/public.php**

```php
p($_['linkShare']);
```

## Thêm ngày expiration trên trang download

Mở file **Apps/Files_Sharing/public.php** thêm dòng

```php
$expiration = $linkItem['expiration'];
```
sau dòng  <code>$shareOwner = $linkItem['uid_owner'];</code>

thêm dòng 

```php
$tmpl->assign('expiration', $expiration); 
```

sau dòng <code>$tmpl->assign('filename', $file);</code>

Trên trang **Apps/Files_Sharing/Templates/public.php**

```php
p($_['expiration']);
```

## Confirm trước khi delete

File thực hiện theo tác delete <code>apps/files/js/fileactions.js </code>

Dòng thực hiện 

```js
element.on('click', {a: null, elem: parent, actionFunc: actions['Delete']}, actionHandler); 
```

```js
element.on('click', function(){
    //alert(1);
    //Show confirm delete
    var modalConfirm = '<div id="modalConfirm" class="modal" data-backdrop="true" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">';
            modalConfirm += '<div class="modal-header">';
                modalConfirm += '<button type="button" class="close" data-dismiss="modal" aria-hidden="true">×</button>';
                modalConfirm += '<h3 id="myModalLabel">';
                    modalConfirm += t('core', 'Confirm Delete');
                modalConfirm += '</h3>';
            modalConfirm += '</div>';
            modalConfirm += '<div class="modal-body">';
                modalConfirm += '<p>';
                    modalConfirm += t('core', 'Are you sure you want to permanently delete this file? You can not undo this action.');
                modalConfirm += '</p>';
            modalConfirm += '</div>';
            modalConfirm += '<div class="modal-footer">';
                modalConfirm += '<button class="btn close-btn" data-dismiss="modal" aria-hidden="true">' + t('core','NO') + '</button>';
                modalConfirm += '<button class="btn btn-primary">'+ t('core','YES') +'</button>';
            modalConfirm += '</div>';
        modalConfirm += '</div>';
        $('#content-wrapper').prepend($(modalConfirm));
            $('#modalConfirm .close').click(function(){
                $('#modalConfirm').remove();
        });
            
        $('#modalConfirm .close-btn').click(function(){
            $('#modalConfirm').remove();
        });

        $('.btn-primary').on('click', {a: null, elem: parent, actionFunc: actions['Delete']}, actionHandler);

        $('.btn-primary').click(function(){
            $('#modalConfirm').remove();
        });
        
    
});
```

## Tự động share file khi upload



Chèn code tuỳ biến vào <code>Apps/files/js/filelist.js</code>

```js
loadingDone:function(name, id)
      // ...
        puropela.shareFile(tr.data('type'),id);
    },
```

Hàm shareFile

```js
function shareFile(itemType,itemSource){
    OC.Share.share(itemType, itemSource, OC.Share.SHARE_TYPE_LINK, '', OC.PERMISSION_READ, function(data) {
        OC.Share.showLink(data.token, null, itemSource);
        OC.Share.updateIcon(itemType, itemSource);
    });
}
```

## Thêm share link trên trang list file

Bổ sung thêm ham lấy tất cả file đã share, **core/ajax/share.php**, đặt ngay sau case **getItemsSharedStatuses**

```
case 'getItemsSharedToken':
        if (isset($_GET['itemType'])) {
            $return = OCP\Share::getItemsShared($_GET['itemType']);
            is_array($return) ? OC_JSON::success(array('data' => $return)) : OC_JSON::error();
        }
        break;
```

## Chèn giá trị vào khi load cùng với icon

Bổ sung hàm **loadIcons** file **core/js/share.js**

```
//Insert share link 
//get shared file 
$.get(OC.filePath('core', 'ajax', 'share.php'), { fetch: 'getItemsSharedToken', itemType: 'file' }, function(result) {
    
    if (result && result.status === 'success'){

            //get token

            $.each(result.data, function(item, listfile){
                
                //chon dong tuong ung

                var $tr = $('#fileList tr').filterAttr('data-id', listfile.file_source);
                //var filename = $tr.filterAttr('data-id', String(listfile.file_source)).data('file');
                //var type = $tr.filterAttr('data-id', String(listfile.file_source)).data('type');

                var link = parent.location.protocol+'//'+location.host+OC.linkTo('', 'public.php')+'?service=files&t='+listfile.token;
                $tr.find('.text-link').val(link);
            });
    }
});
```


## Tuỳ biến khi gởi email

Can thiệp vào hàm file **core/js/share.js**

Dòng 586

```js

$(document).on('submit', '#dropdown #emailPrivateLink', function(event) {
        event.preventDefault();
        var link = $('#linkText').val();
        var itemType = $('#dropdown').data('item-type');
        var itemSource = $('#dropdown').data('item-source');
        var file = $('tr').filterAttr('data-id', String(itemSource)).data('file');
        var email = $('#email').val();
        if (email != '') {
            $('#email').attr('disabled', "disabled");
            $('#email').val(t('core', 'Sending ...'));
            $('#emailButton').attr('disabled', "disabled");

            $.post(OC.filePath('core', 'ajax', 'share.php'), { action: 'email', toaddress: email, link: link, itemType: itemType, itemSource: itemSource, file: file},
                function(result) {
                    $('#email').attr('disabled', "false");
                    $('#emailButton').attr('disabled', "false");
                if (result && result.status == 'success') {
                    $('#email').css('font-weight', 'bold');
                    $('#email').animate({ fontWeight: 'normal' }, 2000, function() {
                        $(this).val('');
                    }).val(t('core','Email sent'));
                } else {
                    OC.dialogs.alert(result.data.message, t('core', 'Error while sharing'));
                }
            });
        }
    });

```























