# Manage image watermarks

Alibaba Cloud Content Delivery Network \(CDN\) supports picture watermarks and text watermarks. You can add picture watermarks and text watermarks to images. This topic describes how to add watermarks to images and provides examples of how to add watermarks to images.

**Note:**

-   This feature is in private preview. To participate in the private preview, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.2020520001.aliyun_topbar.18.dbd44bd3e4f845#/ticket/createIndex).
-   This feature is **free of charge** during the private preview. After it is officially released, it charges fees. For more information, see the product updates.

## Add picture watermarks

Set the action to `watermark`.

The following table describes the parameters.

**Note:**

-   You cannot resize picture watermarks. The size of the base picture that is used as the watermark cannot exceed 1 MB.
-   You can add a maximum of five watermarks to an image. Picture watermarks and text watermarks are supported.

|Feature|Description|Parameter|Valid value|
|-------|-----------|---------|-----------|
|Watermark URL|You can specify watermark URLs that are accessible from the Internet. If authentication or permissions are configured for the specified URL, Alibaba Cloud CDN may fail to access the URL.Watermark URLs must be encoded in Base64. For more information, see [Watermark encoding](#section_xlb_u1r_uk2).

|image|The Base64-encoded string of the specified URL.|

## Add text watermarks

Set the action to `watermark`.

The following table describes the parameters.

**Note:** You can add a maximum of five watermarks to an image. Picture watermarks and text watermarks are supported.

|Feature|Description|Parameter|Valid value|
|-------|-----------|---------|-----------|
|Text content|Specifies the content of a text watermark. The text content must be encoded in Base64. For more information, see [Watermark encoding](#section_xlb_u1r_uk2).|text|The Base64-encoded string of the specified text content. The string can be up to 60 characters in length.|
|Text font|Specifies the font of a text watermark. The font name must be encoded in Base64. For more information, see [Watermark encoding](#section_xlb_u1r_uk2).|type|Up to 10 fonts are supported. For more information, see [Table 1](#table_34s_n6t_ufa).**Note:** If you use a font that is not included in the 10 fonts, the system identifies it as the default font alihyaihei. |
|Text color|Specifies the color of a text watermark. Valid values are RGB color values.|color|RGB color values. For example, 000000 represents black and FFFFFF represents white. Default value: 000000. A value of 000000 indicates that the color of the text is black. |
|Text rotation|Specifies the angle to which the text is rotated clockwise.|rotate|Supported angles are 90°, 180°, and 270°.|
|Text tiling|Specifies whether to tile an image with text watermarks.|fill|Valid values: 0 and 1. Default value: 0.-   0: does not tile the image with text watermarks.
-   1: tiles the image with text watermarks. |

The following table describes the text fonts supported by Alibaba Cloud CDN.

|Text fonts|Description|Encoded value|
|----------|-----------|-------------|
|alihyaihei|A bold font. This is the default font.|YWxpaHlhaWhlaQ|
|hysong|A Songti font.|aHlzb25n|
|hyhei|A Heiti font.|aHloZWk|
|hyshuangxian|A double line font.|aHlzaHVhbmd4aWFu|
|fzltzhk|A Heiti font.|ZnpsdHpoaw|
|fzshengsks|A regular script font.|ZnpzaGVuZ3Nrcw|
|fzqusongjian|A Songti font.|ZnpxdXNvbmdqaWFu|
|zzgfxingyan|An artistic font.|enpnZnhpbmd5YW4|
|comfortaa|Comfortaa|Y29tZm9ydGFh|
|notosans|NotoSans|bm90b3NhbnM|

## Watermark positions

Picture watermarks and text watermarks can be positioned by a 3 by 3 grid and Cartesian coordinates \(x,y\). You can use the 3 by 3 grid and Cartesian coordinates to adjust the position of each watermark. This way, you can manage the layout of watermarks. The following figure shows the positions of watermarks based on a 3 by 3 grid and Cartesian coordinates.

![Watermark positions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4900397061/p186559.png)

|Parameter|Description|Valid value|
|---------|-----------|-----------|
|t|Specifies the opacity of the text or image watermark.|\[0,100\] Default value: 100. A value of 100 indicates that the watermark is opaque. |
|g|Specifies the position of the watermark on the image.|-   nw: upper-left
-   north: upper-center
-   ne: upper-right
-   west: center-left
-   center: center
-   east: center-right
-   sw: lower-left
-   south: lower-center
-   se: lower-right

For more information about the positions, see the preceding figure.|
|x|Specifies the horizontal margin, which is the horizontal distance between the watermark and the left edge of the image. This parameter takes effect only when the watermark is on the upper-left, center-left, lower-left, upper-right, center-right, or lower-right side of the image.|\[0,4096\] Default value: 10. Unit: pixels. |
|y|Specifies the vertical margin, which is the vertical distance between the watermark and the lower edge of the image. This parameter takes effect only when the watermark is on the upper-left, center-left, lower-left, upper-right, center-right, or lower-right side of the image.|\[0,4096\] Default value: 10. Unit: pixels. |

## Watermark encoding

When you add watermarks to an image, the content, color, and font of text watermarks and the name of picture watermarks must be URL-encoded in Base64. The encoding method is:

1.  Encode the content in Base64.
2.  Replace the encoded content based on the following rules:
    -   Replace the plus signs \(+\) with hyphens \(-\).
    -   Replace the forward slashes \(/\) with underscores \(\_\).
    -   Omit the equal signs \(=\) that are at the end of strings.

We recommend that you use [URL-safe Baes64 encoding tools](https://simplycalc.com/base64url-encode.php) to encode the content, color, and font of text watermarks and the name of picture watermark.

**Note:** The encoded strings of watermarks can be used only in parameters used to add watermarks. Do not include the encoded strings of watermarks in signature strings.

