---
title: Dynamische Recordset-Eigenschaften in XML | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d9d19ded093cd10a7670b31cd2d5c78a475950d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760966"
---
# <a name="recordset-dynamic-properties-in-xml"></a>Dynamische Recordseteigenschaften in XML
Die folgenden recordsetanbieter-spezifischen Eigenschaften (von der Client Cursor-Engine) werden derzeit im XML-Format beibehalten:  
  
-   Neusynchronisierung aktualisieren  
  
-   Eindeutige Tabelle  
  
-   Eindeutiges Schema  
  
-   Eindeutiger Katalog  
  
-   Befehl zum erneuten Synchronisieren  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   Updatecriteria  
  
-   Name der erneuten Form  
  
-   Autorecalc  
  
 Diese Eigenschaften werden im Schema Abschnitt als Attribute der Element Definition für das Recordset gespeichert, das gespeichert wird. Diese Attribute werden im Rowset-Schema Namespace definiert und müssen das Präfix "RS:" aufweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
