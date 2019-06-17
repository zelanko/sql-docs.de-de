---
title: Verweis auf die ADO-Bibliotheken In Visual C++-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7eb96d739a95e1b75894ab3f561f6db3c6661a21
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699826"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Verweis auf die ADO-Bibliotheken in Visual C++-Anwendungen
Um die neueste Version von ADO in Visual C++-Anwendung verwenden zu können, verwenden Sie die folgenden `#import` Richtlinie:  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Um ADO MD oder ADOX verwenden, müssen Sie importieren *msadomd.dll* oder *msadox.dll*, mithilfe der oben aufgeführten Syntax.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Um eine frühere Version von ADO verwenden, ersetzen *"MSADO15.dll"* oben mit einem der folgenden Typbibliotheken.  
  
-   *msado27.tlb*, ADO 2.7 Typbibliothek.  
  
-   *msado26.tlb*, ADO 2.6-Typbibliothek  
  
-   *msado25.tlb*, ADO-2,5-Typbibliothek  
  
-   *MSADO21.tlb*, ADO 2.1 Typbibliothek.  
  
-   *msado20.tlb*, ADO-2.0-Typbibliothek
