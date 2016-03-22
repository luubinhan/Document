# Link to page

```
<a class="downloadBut" href="<?php echo get_permalink(1422); ?>?link=<?php echo $post->guid; ?>">Download</a>
```

# Template

```
/**
 * Template Name: Force Download
 *
 */


$fileUrl = $_GET['link'];
if ($fileUrl != "") {
    header("Content-Type: application/octet-stream");
    header("Content-Transfer-Encoding: Binary");
    header('Content-Disposition: attachment; filename="'.basename($fileUrl).'"');
    echo readfile($fileUrl);
}
```