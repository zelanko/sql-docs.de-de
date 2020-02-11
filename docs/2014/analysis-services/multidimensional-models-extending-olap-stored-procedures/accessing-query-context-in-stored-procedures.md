---
title: Zugreifen auf den Abfrage Kontext in gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93624a612126e9103144b8b53272122e66202b8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702667"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Zugreifen auf den Abfragekontext in gespeicherten Prozeduren
  Der Ausführungskontext einer gespeicherten Prozedur steht innerhalb des Codes der gespeicherten Prozedur als `Context`-Objekt des ADOMD.NET-Serverobjektmodells zur Verfügung. Der Kontext ist schreibgeschützt und kann nicht von der gespeicherten Prozedur geändert werden. Für dieses Objekt stehen die folgenden Eigenschaften zur Verfügung.  
  
|Eigenschaft|type|BESCHREIBUNG|  
|--------------|----------|-----------------|  
|**CURRENTCUBE**|Cube|Der Cube für den aktuellen Abfragekontext.|  
|**CurrentDatabaseName**|String|Der Bezeichner der aktuellen Datenbank.|  
|**CurrentConnection**|Verbindung|Ein Verweis auf das Verbindungsobjekt im aktuellen Kontext.|  
|**Tage**|Integer|Die Durchlaufnummer für den aktuellen Kontext.|  
  
 Das `Context`-Objekt ist vorhanden, wenn das MDX-Objektmodell (Multidimensional Expressions) in einer gespeicherten Prozedur verwendet wird. Es ist nicht verfügbar, wenn das MDX-Objektmodell auf einem Client verwendet wird. Das `Context`-Objekt wird nicht explizit an die gespeicherte Prozedur übergeben bzw. von ihr zurückgegeben. Es ist während der Ausführung der gespeicherten Prozedur verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellen](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren von gespeicherten Prozeduren](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
