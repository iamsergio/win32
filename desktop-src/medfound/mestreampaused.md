﻿---
Description: 'Raised by a media stream when the IMFMediaSource::Pause method completes asynchronously.'
ms.assetid: '8fafb9a1-95a4-44b6-acd6-fb007d515915'
title: MEStreamPaused event
---

# MEStreamPaused event

Raised by a media stream when the [**IMFMediaSource::Pause**](imfmediasource-pause.md) method completes asynchronously.

## Event values

Possible values retrieved from [**IMFMediaEvent::GetValue**](imfmediaevent-getvalue.md) include the following.



| VARTYPE              | Description                           |
|----------------------|---------------------------------------|
| VT\_EMPTY<br/> | No event data.<br/> <br/> |



## Remarks

Each active stream in the presentation sends this event.

## Requirements



|                                     |                                                                                                          |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                                           |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                                     |
| Header<br/>                   | <dl> <dt>Mfobjects.h (include Mfidl.h)</dt> </dl> |



## See also

<dl> <dt>

[Media Foundation Events](media-foundation-events.md)
</dt> </dl>

 

 



