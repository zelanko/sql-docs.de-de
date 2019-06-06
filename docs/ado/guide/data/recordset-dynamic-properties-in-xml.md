---
title: Recordset Dynamic-Eigenschaften in XML | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b58a9463932e9761688fd744b972f50ad3286381
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718686"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Dynamische Recordseteigenschaften in XML
Die folgenden Eigenschaften des Recordsetziels anbieterspezifische (aus der Client-Cursor-Engine) werden derzeit in der XML-Format gespeichert:  
  
-   Aktualisieren Sie die erneute Synchronisierung  
  
-   Eindeutige Tabelle  
  
-   Eindeutiges Schema  
  
-   Eindeutige Katalogressource  
  
-   Resync-Befehl  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   Reshape Name  
  
-   AutoRecalc  
  
 Diese Eigenschaften werden als Attribute der Definition des Elements für das Recordset beibehalten wird im Schema-Abschnitt gespeichert. Diese Attribute sind in der Rowset-Schema-Namespace definiert und müssen das Präfix "Rs:".  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
