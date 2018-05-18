---
Description: 'How symbolic links affect standard file functions that use path names to specify one or more files.'
ms.assetid: 'afda53eb-d0db-4844-9dd0-8a7d93ca341f'
title: Symbolic Link Effects on File Systems Functions
---

# Symbolic Link Effects on File Systems Functions

Several standard file functions that use path names to specify one or more files are affected by the use of symbolic links. This topic lists those functions and describes the changes in behavior:

-   [CopyFile and CopyFileTransacted](#copyfile-and-copyfiletransacted)
-   [CopyFileEx](#copyfileex)
-   [CreateFile and CreateFileTransacted](#createfile-and-createfiletransacted)
-   [CreateHardLink and CreateHardLinkTransacted](#createhardlink-and-createhardlinktransacted)
-   [DeleteFile and DeleteFileTransacted](#deletefile-and-deletefiletransacted)
-   [FindFirstChangeNotification](#findfirstchangenotification)
-   [FindFirstFile and FindFirstFileTransacted](#findfirstfile-and-findfirstfiletransacted)
-   [FindFirstFileEx](#findfirstfileex)
-   [FindNextFile](#findnextfile)
-   [GetBinaryType](#getbinarytype)
-   [GetCompressedFileSize and GetCompressedFileSizeTransacted](#getcompressedfilesize-and-getcompressedfilesizetransacted)
-   [GetDiskFreeSpace](#getdiskfreespaceex)
-   [GetDiskFreeSpaceEx](#getdiskfreespaceex)
-   [GetFileAttributes](#getfileattributesex)
-   [GetFileAttributesEx](#getfileattributesex)
-   [GetFileSecurity](#getfilesecurity)
-   [GetTempPath](#gettemppath)
-   [GetVolumeInformation](#getvolumeinformation)
-   [SetFileAttributes](#setfileattributes)
-   [SetFileSecurity](#setfilesecurity)
-   [Related topics](#related-topics)

In the descriptions below, the following terms are used:

-   Source file—The original file that is to be copied.
-   Destination file—The newly created copy of the file.
-   Target—The entity that a symbolic link points to.

> [!Note]  
> The behavior of functions that accept a handle created using the [**CreateFile**](createfile.md) function, such as the [**GetFileTime**](https://msdn.microsoft.com/library/windows/desktop/ms724320) function, will differ based on whether or not the **CreateFile** function was called using the **FILE\_FLAG\_OPEN\_REPARSE\_POINT** flag. For more information, see [**CreateFile**](createfile.md) and the following [CreateFile and CreateFileTransacted](#createfile-and-createfiletransacted) section.

 

## CopyFile and CopyFileTransacted

If the source file is a symbolic link, the actual file copied is the target of the symbolic link.

If the destination file already exists and is a symbolic link, the symbolic link is overwritten by the source file.

## CopyFileEx

If **COPY\_FILE\_COPY\_SYMLINK** is specified and:

-   If the source file is a symbolic link, the symbolic link is copied, not the target file.
-   If the source file is not a symbolic link, there is no change in behavior.
-   If the destination file is an existing symbolic link, the symbolic link is overwritten, not the target file.
-   If **COPY\_FILE\_FAIL\_IF\_EXISTS** is also specified, and the destination file is an existing symbolic link, the operation fails in all cases.

If **COPY\_FILE\_COPY\_SYMLINK** is not specified and:

-   If **COPY\_FILE\_FAIL\_IF\_EXISTS** is also specified, and the destination file is an existing symbolic link, the operation fails only if the target of the symbolic link exists.
-   If **COPY\_FILE\_FAIL\_IF\_EXISTS** is not specified, there is no change in behavior.

**Windows Server 2003 and Windows XP:** The **COPY\_FILE\_COPY\_SYMLINK** flag is not supported. If the source file is a symbolic link, the actual file copied is the target of the symbolic link.

## CreateFile and CreateFileTransacted

If the call to this function creates a new file, there is no change in behavior.

If **FILE\_FLAG\_OPEN\_REPARSE\_POINT** is specified and:

-   If an existing file is opened and it is a symbolic link, the handle returned is a handle to the symbolic link.
-   If **CREATE\_ALWAYS**, **TRUNCATE\_EXISTING**, or **FILE\_FLAG\_DELETE\_ON\_CLOSE** are specified, the file affected is a symbolic link.

If **FILE\_FLAG\_OPEN\_REPARSE\_POINT** is not specified and:

-   If an existing file is opened and it is a symbolic link, the handle returned is a handle to the target.
-   If **CREATE\_ALWAYS**, **TRUNCATE\_EXISTING**, or **FILE\_FLAG\_DELETE\_ON\_CLOSE** are specified, the file affected is the target.

## CreateHardLink and CreateHardLinkTransacted

If the path points to a symbolic link, the function creates a hard link to the target.

## DeleteFile and DeleteFileTransacted

If the path points to a symbolic link, the symbolic link is deleted, not the target. To delete a target, you must call [**CreateFile**](createfile.md) and specify **FILE\_FLAG\_DELETE\_ON\_CLOSE**.

## FindFirstChangeNotification

If the path points to a symbolic link, the notification handle is created for the target. If an application has registered to receive change notifications for a directory that contains symbolic links, the application is only notified when the symbolic links have been changed, not the target files.

## FindFirstFile and FindFirstFileTransacted

If the path points to a symbolic link, the [**WIN32\_FIND\_DATA**](win32-find-data-str.md) buffer contains information about the symbolic link, not the target.

## FindFirstFileEx

If the path points to a symbolic link, the [**WIN32\_FIND\_DATA**](win32-find-data-str.md) buffer contains information about the symbolic link, not the target.

## FindNextFile

If the path points to a symbolic link, the [**WIN32\_FIND\_DATA**](win32-find-data-str.md) buffer contains information about the symbolic link, not the target.

## GetBinaryType

If the path points to a symbolic link, the target file is used.

## GetCompressedFileSize and GetCompressedFileSizeTransacted

If the path points to a symbolic link, the function returns the file size of the target.

## GetDiskFreeSpace

If the path points to a symbolic link, the operation is performed on the target.

## GetDiskFreeSpaceEx

If the path points to a symbolic link, the operation is performed on the target.

## GetFileAttributes

If the path points to a symbolic link, the function returns attributes for the symbolic link.

## GetFileAttributesEx

If the path points to a symbolic link, the function returns attributes for the symbolic link.

## GetFileSecurity

If the path points to a symbolic link, the function returns attributes for the symbolic link.

## GetTempPath

If the path points to a symbolic link, the temp path name maintains any symbolic links.

## GetVolumeInformation

If the path points to a symbolic link, the function returns volume information for the target.

## SetFileAttributes

If the path points to a symbolic link, the function retrieves attributes for the symbolic link.

## SetFileSecurity

If the path points to a symbolic link, the function returns attributes for the symbolic link.

## Related topics

<dl> <dt>

[**CopyFile**](copyfile.md)
</dt> <dt>

[**CopyFileTransacted**](copyfiletransacted.md)
</dt> <dt>

[**CopyFileEx**](copyfileex.md)
</dt> <dt>

[**CreateFile**](createfile.md)
</dt> <dt>

[**CreateFileTransacted**](createfiletransacted.md)
</dt> <dt>

[**CreateHardLink**](createhardlink.md)
</dt> <dt>

[**CreateHardLinkTransacted**](createhardlinktransacted.md)
</dt> <dt>

[**DeleteFile**](deletefile.md)
</dt> <dt>

[**DeleteFileTransacted**](deletefiletransacted.md)
</dt> <dt>

[**FindFirstChangeNotification**](findfirstchangenotification.md)
</dt> <dt>

[**FindFirstFile**](findfirstfile.md)
</dt> <dt>

[**FindFirstFileEx**](findfirstfileex.md)
</dt> <dt>

[**FindFirstFileTransacted**](findfirstfiletransacted.md)
</dt> <dt>

[**FindNextFile**](findnextfile.md)
</dt> <dt>

[**GetBinaryType**](getbinarytype.md)
</dt> <dt>

[**GetCompressedFileSize**](getcompressedfilesize.md)
</dt> <dt>

[**GetCompressedFileSizeTransacted**](getcompressedfilesizetransacted.md)
</dt> <dt>

[**GetDiskFreeSpace**](getdiskfreespace.md)
</dt> <dt>

[**GetDiskFreeSpaceEx**](getdiskfreespaceex.md)
</dt> <dt>

[**GetFileAttributes**](getfileattributes.md)
</dt> <dt>

[**GetFileAttributesEx**](getfileattributesex.md)
</dt> <dt>

[**GetFileSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa446639)
</dt> <dt>

[**GetTempPath**](gettemppath.md)
</dt> <dt>

[**GetVolumeInformation**](getvolumeinformation.md)
</dt> <dt>

[**SetFileAttributes**](setfileattributes.md)
</dt> <dt>

[**SetFileSecurity**](https://msdn.microsoft.com/library/windows/desktop/aa379577)
</dt> </dl>

 

 


