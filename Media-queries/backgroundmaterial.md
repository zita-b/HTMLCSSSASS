<meta> tag viewport

with it we can control the viewport's size and shape
the browser's **viewport** is the area of the window in which web content can be seen. If it is not the same size as the **rendered page**, the browser provides scrollbars

The **virtual viewport** is a way to make non-mobile-optimized sites look better on narrow screen devices (some mobile devices and other narrow screens render pages in a virtual viewport which is usually wider than the screen and then shrink the rendered result down to fit the page)
This mechanism is not so good for pages that are optimized for narrow screens using media queries because the set media queries might never kick in. The viewport meta tag mitigates this problem of virtual viewport on narrow screen devices.

a typical mobile optimized site contains something like the following:

**<meta name="viewport" content="width=device-width, initial-scale=1">**

viewport meta tag properties:

**width** controls the size of the viewport, it can be set to a specific number of pixels (width=600) or to the special **device-width**, devide-width equals 100vw or 100% of the viewport width. Minimum 1, maximum 10000.

**height** same as width, can be set to a specific value in pixels or **device-height**

**initial-scale** controls the zoom level when the page is first loaded. Minimum: 0.1 maximum 10, default 1.

**minimum-scale** controls how much zoom out is allowed on the page. Minimum: 0.1, maximum: 10, default 0.1

**maximum-scale** controls allowed zoom in, any value less than 3 fails accessibility. Minimum 0,1 maximum 10 default 10.

**user-scalable** controls whether zoom in and zoom out is allowed on the page, 0, 1, yes or no. default 1 (yes).

