---
title: Verweisen auf die ADO-Bibliotheken in einer Visual C++ Anwendung | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a790ace40aa31324ce8b22127d8f6948ae86e059
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764761"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Verweis auf die ADO-Bibliotheken in Visual C++-Anwendungen
Verwenden Sie die folgende Direktive, um die neueste Version von ADO in einer Visual C++ Anwendung zu verwenden `#import` :  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Um ADO MD oder ADOX verwenden zu können, müssen Sie *msadomd. dll* oder *Msadox. dll*importieren, indem Sie die oben beschriebene Syntax verwenden.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Um eine frühere Version von ADO zu verwenden, ersetzen Sie *"MSADO15. dll* oben durch eine der folgenden Typbibliotheken.  
  
-   *msado27. tlb*, ADO 2,7-Typbibliothek  
  
-   *msado26. tlb*, ADO 2,6-Typbibliothek  
  
-   *msado25. tlb*, ADO 2,5-Typbibliothek  
  
-   *MSADO21. tlb*, ADO 2,1-Typbibliothek  
  
-   *msado20. tlb*, ADO 2,0-Typbibliothek
