---
title: "tmpnam_s, _wtmpnam_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-standard-libraries"]
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: ["tmpnam_s", "_wtmpnam_s"]
apilocation: ["msvcrt.dll", "msvcr80.dll", "msvcr90.dll", "msvcr100.dll", "msvcr100_clr0400.dll", "msvcr110.dll", "msvcr110_clr0400.dll", "msvcr120.dll", "msvcr120_clr0400.dll", "ucrtbase.dll", "api-ms-win-crt-stdio-l1-1-0.dll"]
apitype: "DLLExport"
f1_keywords: ["tmpnam_s", "_wtmpnam_s", "L_tmpnam_s"]
dev_langs: ["C++"]
helpviewer_keywords: ["tmpnam_s function", "file names [C++], creating temporary", "_wtmpnam_s function", "L_tmpnam_s constant", "temporary files, creating", "file names [C++], temporary", "wtmpnam_s function"]
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpnam_s, _wtmpnam_s
Generate names you can use to create temporary files. These are versions of [tmpnam and _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) with security enhancements as described in [Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Syntax  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### Parameters  
 [out] `str`  
 Pointer that will hold the generated name.  
  
 [in] `sizeInChars`  
 The size of the buffer in characters.  
  
## Return Value  
 Both of these functions return 0 if successful or an error number on failure.  
  
### Error Conditions  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**Return Value**|**Contents of**  `str`|  
|`NULL`|any|`EINVAL`|not modified|  
|not `NULL` (points to valid memory)|too short|`ERANGE`|not modified|  
  
 If `str` is `NULL`, the invalid parameter handler is invoked, as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL` and return `EINVAL`.  
  
## Remarks  
 Each of these functions returns the name of a file that does not currently exist. `tmpnam_s` returns a name unique in the current working directory. Note than when a file name is pre-pended with a backslash and no path information, such as \fname21, this indicates that the name is valid for the current working directory.  
  
 For `tmpnam_s`, you can store this generated file name in `str`. The maximum length of a string returned by `tmpnam_s` is `L_tmpnam_s`, defined in STDIO.H. If `str` is `NULL`, then `tmpnam_s` leaves the result in an internal static buffer. Thus any subsequent calls destroy this value. The name generated by `tmpnam_s` consists of a program-generated file name and, after the first call to `tmpnam_s`, a file extension of sequential numbers in base 32 (.1-.1vvvvvu, when `TMP_MAX_S` in STDIO.H is INT_MAX).  
  
 `tmpnam_s` automatically handles multibyte-character string arguments as appropriate, recognizing multibyte-character sequences according to the OEM code page obtained from the operating system. `_wtmpnam_s` is a wide-character version of `tmpnam_s`; the argument and return value of `_wtmpnam_s` are wide-character strings. `_wtmpnam_s` and `tmpnam_s` behave identically except that `_wtmpnam_s` does not handle multibyte-character strings.  
  
 In C++, using these functions is simplified by template overloads; the overloads can infer buffer length automatically, eliminating the need to specify a size argument. For more information, see [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### Generic-Text Routine Mappings  
  
|TCHAR.H routine|_UNICODE & _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`tmpnam_s`|\<stdio.h>|  
|`_wtmpnam_s`|\<stdio.h> or \<wchar.h>|  
  
 For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## See Also  
 [Stream I/O](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)