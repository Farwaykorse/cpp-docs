---
title: "propput | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-windows"]
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: ["vc-attr.propput"]
dev_langs: ["C++"]
helpviewer_keywords: ["propput attribute"]
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# propput
Specifies a property setting function.  
  
## Syntax  
  
```  
  
[propput]  
  
```  
  
## Remarks  
 The **propput** C++ attribute has the same functionality as the [propput](http://msdn.microsoft.com/library/windows/desktop/aa367146) MIDL attribute.  
  
## Example  
 See the example for [bindable](../windows/bindable.md) for a sample use of **propput**.  
  
## Requirements  
  
### Attribute Context  
  
|||  
|-|-|  
|**Applies to**|Method|  
|**Repeatable**|No|  
|**Required attributes**|None|  
|**Invalid attributes**|**propget**, **propputref**|  
  
 For more information about the attribute contexts, see [Attribute Contexts](../windows/attribute-contexts.md).  
  
## See Also  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propputref](../windows/propputref.md)