---
title: "Compiler Error C2377 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-tools"]
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: ["C2377"]
dev_langs: ["C++"]
helpviewer_keywords: ["C2377"]
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2377
'identifier' : redefinition; typedef cannot be overloaded with any other symbol  
  
 A `typedef` identifier is redefined.  
  
 The following sample generates C2377:  
  
```  
// C2377.cpp  
// compile with: /c  
typedef int i;  
int i;   // C2377  
int j;   // OK  
```