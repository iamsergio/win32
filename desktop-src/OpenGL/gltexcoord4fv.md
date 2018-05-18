---
title: glTexCoord4fv function
description: Sets the current texture coordinates.
ms.assetid: '973d3177-8e94-4a95-ba88-e9e33f5c0a5f'
keywords: ["glTexCoord4fv function OpenGL"]
topic_type:
- apiref
api_name:
- glTexCoord4fv
api_location:
- opengl32.dll
api_type:
- DllExport
---

# glTexCoord4fv function

Sets the current texture coordinates.

## Syntax


```C++
void WINAPI glTexCoord4fv(
  �const GLfloat *v
);
```



## Parameters

<dl> <dt>

*v* 
</dt> <dd>

A pointer to an array of four elements, which in turn specifies the s, t, r, and q texture coordinates.

</dd> </dl>

## Return value

This function does not return a value.

## Remarks

The [**glTexCoord**](gltexcoord-functions.md) function sets the current texture coordinates that are part of the data associated with polygon vertices. The **glTexCoord** function specifies texture coordinates in one, two, three, or four dimensions. The glTexCoord1 function sets the current texture coordinates to (s, 0, 0, 1); a call to glTexCoord2 sets them to (s, t, 0, 1). Similarly, glTexCoord3 specifies the texture coordinates as (s, t, r, 1), and glTexCoord4 defines all four components explicitly as (s, t, r, q). You can update the current texture coordinates at any time. In particular, you can call glTexCoord between a call to [**glBegin**](glbegin.md) and the corresponding call to [**glEnd**](glend.md). The following function retrieves information related to **glTexCoord**:

[**glGet**](glgetbooleanv--glgetdoublev--glgetfloatv--glgetintegerv.md) with argument GL\_CURRENT\_TEXTURE\_COORDS

## Requirements



|                                     |                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�2000 Professional \[desktop apps only\]<br/>                              |
| Minimum supported server<br/> | Windows�2000 Server \[desktop apps only\]<br/>                                    |
| Header<br/>                   | <dl> <dt>Gl.h</dt> </dl>         |
| Library<br/>                  | <dl> <dt>Opengl32.lib</dt> </dl> |
| DLL<br/>                      | <dl> <dt>Opengl32.dll</dt> </dl> |



## See also

<dl> <dt>

[glVertex](glvertex-functions.md)
</dt> </dl>

�

�




