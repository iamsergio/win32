---
Description: A region is a portion of the display surface.
ms.assetid: eb78d7a0-6293-487f-88c5-88ba455b965f
title: Regions
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Regions

A region is a portion of the display surface. Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves). The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.

![illustration showing a transparent rectangular region overlapping an opaque curved shape](images/aboutgdip02-art27.png)

Regions are often used for clipping and hit testing. Clipping involves restricting drawing to a certain region of the screen, usually the portion of the screen that needs to be updated. Hit testing involves checking to see whether the cursor is in a certain region of the screen when a mouse button is pressed.

You can construct a region from a rectangle or from a path. You can also create complex regions by combining existing regions. The [**Region**](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-region) class provides the following methods for combining regions: [Intersect](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-intersect(in const graphicspath)), [Union](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-union(in const graphicspath)), [Xor](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-xor(in const graphicspath)), [Exclude](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-exclude(in const graphicspath)), and [**Region::Complement**](https://msdn.microsoft.com/en-us/library/ms534829(v=VS.85).aspx).

The intersection of two regions is the set of all points belonging to both regions. The union is the set of all points belonging to one or the other or both regions. The complement of a region is the set of all points that are not in the region. The following illustration shows the intersection and union of the two regions in the previous figure.

![illustration showing the intersection of the regions in the previous illustration, and their intersection](images/aboutgdip02-art28.png)

The [Xor](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-xor(in const graphicspath)) method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both. The [Exclude](/windows/desktop/api/gdiplusheaders/nf-gdiplusheaders-region-exclude(in const graphicspath)) method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region. The following illustration shows the regions that result from applying the Xor and Exclude methods to the two regions shown at the beginning of this topic.

![illustration showing the parts in either region but not both, and the part of the rectangle that does not overlap the curved region](images/aboutgdip02-art29.png)

To fill a region, you need a [**Graphics**](/windows/desktop/api/gdiplusgraphics/nl-gdiplusgraphics-graphics) object, a [**Brush**](/windows/desktop/api/gdiplusbrush/nl-gdiplusbrush-brush) object, and a [**Region**](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-region) object. The **Graphics** object provides the [**Graphics::FillRegion**](/windows/desktop/api/Gdiplusgraphics/nf-gdiplusgraphics-graphics-fillregion) method, and the **Brush** object stores attributes of the fill, such as color or pattern. The following example fills a region with a solid color.


```
myGraphics.FillRegion(&amp;mySolidBrush, &amp;myRegion);
```



 

 


