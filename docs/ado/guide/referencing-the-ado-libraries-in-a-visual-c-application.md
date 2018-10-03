---
title: Verweis auf die ADO-Bibliotheken In Visual C++-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
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
manager: craigg
ms.openlocfilehash: fa07fc475d423cf4c338d40393c053d1dc30d488
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601988"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Verweis auf die ADO-Bibliotheken in Visual C++-Anwendungen
Um die neueste Version von ADO in Visual C++-Anwendung verwenden zu können, verwenden Sie die folgenden `#import` Richtlinie:  
  
```  
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
