---
title: XSL-Zwischenspeichern (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 64256db5e8cb147c47e28852bb3589e8732bf9c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256012"
---
# <a name="xsl-caching-sqlxml-40"></a>XSL-Zwischenspeichern (SQLXML 4.0)
  Das Zwischenspeichern von XSL-Stylesheets verbessert die Leistung. Bei der ersten Ausführung bleibt ein XSL-Stylesheet im Arbeitsspeicher, wenn das XSL-Zwischenspeichern auf ON festgelegt wurde. Dies verbessert die Leistung bei der nachfolgenden Verarbeitung. Die Standardeinstellung ist ON.  
  
 Sie können die XSL-Cachegröße festlegen, indem Sie den folgenden Schlüssel in der Registrierung hinzufügen:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Die XSL-Cachegröße sollte auf Basis des vorhandenen Arbeitsspeichers und der Anzahl der von Ihnen verwendeten XSL-Stylesheets festgelegt werden. Der Standardwert von **XSLCacheSize** lautet 31. Sie können die Cachegröße erhöhen, wenn der XSL-Zugriff langsam erscheint, oder die Cachegröße verringern, wenn der Arbeitsspeicher zu gering ist.  
  
 Für bessere Leistung wird empfohlen, dass Sie **XSLCacheSize** auf einen höheren Wert als die Anzahl der von Ihnen üblicherweise verwendeten XSL-Stylesheets festlegen. Wenn **XSLCacheSize** auf einen niedrigeren Wert als die Anzahl Ihrer XSL-Stylesheets festgelegt ist, sinkt die Leistung mit zunehmender Anzahl von XSL-Stylesheets. Der **XSLCacheSize** kann auf ein Maximum von 128 festgelegt werden.  
  
 Jedes Mal, wenn das zwischengespeicherte XSL-Stylesheet verwendet wird, wird die Änderungszeit der XSL-Datei überprüft, um festzustellen, ob sie aktualisiert werden muss. Das liegt daran, dass die Datenträgerkopie neuer als die Cachekopie ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Zwischenspeichern von Vorlagen &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [Das Zwischenspeichern von Schemas &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
  
  
