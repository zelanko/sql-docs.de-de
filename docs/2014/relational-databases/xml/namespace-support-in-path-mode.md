---
title: Namespaceunterstützung im PATH-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f75a1a1281ba482935a264c2e5bdac6e6bb290e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297570"
---
# <a name="namespace-support-in-path-mode"></a>Namespaceunterstützung im PATH-Modus
  Die Unterstützung von Namespaces im PATH-Modus wird durch den Einsatz von WITH NAMESPACES bereitgestellt. Beispielsweise zeigt die folgende Abfrage die Syntax von WITH NAMESPACES, um einen Namespace ("a:") zu deklarieren, der in der nachfolgenden SELECT-Anweisung verwendet werden kann:  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Beispiele  
 Diese Beispiele veranschaulichen die Verwendung des PATH-Modus beim Generieren von XML-Code aus einer SELECT-Abfrage. Viele dieser Abfragen beziehen sich auf die XML-Dokumente mit den Fahrradfertigungsanweisungen, die in der Instructions-Spalte der ProductModel-Tabelle gespeichert sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)  
  
  
