﻿---
Description: 'Creates a copy of an effect.'
ms.assetid: '6272bce0-b712-4a61-afe2-8f572993b03e'
title: 'ID3DXEffect::CloneEffect method'
---

# ID3DXEffect::CloneEffect method

Creates a copy of an effect.

## Syntax


```C++
HRESULT CloneEffect(
  [in]  LPDIRECT3DDEVICE9 pDevice,
  [out] LPD3DXEFFECT      *ppEffect
);
```



## Parameters

<dl> <dt>

*pDevice* \[in\]
</dt> <dd>

Type: **[**LPDIRECT3DDEVICE9**](idirect3ddevice9.md)**

Pointer to an [**IDirect3DDevice9**](idirect3ddevice9.md) interface, representing the device associated with the effect.

</dd> <dt>

*ppEffect* \[out\]
</dt> <dd>

Type: **[**LPD3DXEFFECT**](id3dxeffect.md)\***

Pointer to an [**ID3DXEffect**](id3dxeffect.md) interface, containing the cloned effect.

</dd> </dl>

## Return value

Type: **[**HRESULT**](455d07e9-52c3-4efb-a9dc-2955cbfd38cc)**

If the method succeeds, the return value is S\_OK. If the method fails, the return value can be one of the following: D3DERR\_INVALIDCALL, D3DXERR\_INVALIDDATA.

## Remarks

> [!Note]  
> This function will not clone an effect if the user specifies [D3DXFX\_NOT\_CLONEABLE](d3dxfx.md) during effect creation.

 

To update shared and non-shared parameters in an active technique of a cloned effect, see [**ID3DXEffect::CommitChanges**](id3dxeffect--commitchanges.md).

## Requirements



|                    |                                                                                          |
|--------------------|------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX9Effect.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3dx9.lib</dt> </dl>     |



## See also

<dl> <dt>

[ID3DXEffect](id3dxeffect.md)
</dt> </dl>

 

 



