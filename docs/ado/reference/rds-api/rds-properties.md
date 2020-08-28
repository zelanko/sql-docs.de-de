---
description: RDS-Eigenschaften
title: RDS-Eigenschaften | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- RDS properties [ADO]
- properties [ADO], RDS
ms.assetid: e4e04cbd-21fc-44a1-9f21-49aa68746934
author: rothja
ms.author: jroth
ms.openlocfilehash: a4f47967fc80ba488c57299fe7f94c13d9f9e949
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981521"
---
# <a name="rds-properties"></a>RDS-Eigenschaften
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
|Eigenschaft|Beschreibung|  
|-|-|  
|[Verbinden (RDS)](./connect-property-rds.md)|Gibt den Datenbanknamen an, von dem die Abfrage-und Aktualisierungs Vorgänge ausgeführt werden.|  
|[ExecuteOptions (RDS)](./executeoptions-property-rds.md)|Gibt an, ob die asynchrone Ausführung aktiviert ist.|  
|[FetchOptions (RDS)](./fetchoptions-property-rds.md)|Gibt den Typ des asynchronen fetchen an.|  
|[FilterColumn (RDS)](./filtercolumn-property-rds.md)|Gibt die Spalte an, für die die Filterkriterien ausgewertet werden sollen.|  
|[Filter Kriterium (RDS)](./filtercriterion-property-rds.md)|Gibt den Auswertungs Operator an, der im Filter Wert verwendet werden soll.|  
|[FilterValue (RDS)](./filtervalue-property-rds.md)|Gibt den Wert an, mit dem Datensätze gefiltert werden.|  
|[Handler (RDS)](./handler-property-rds.md)|Gibt den Namen eines serverseitigen Anpassungsprogramms (*Handler*) an, das die Funktionalität von **RDSServer. DataFactory**erweitert, sowie alle Parameter, die vom *Handler*verwendet werden.|  
|[InternetTimeout (RDS)](./internettimeout-property-rds.md)|Gibt die Anzahl der Millisekunden an, die gewartet wird, bevor ein Timeout für eine Anforderung eintritt.|  
|["Read ystate" (RDS)](./readystate-property-rds.md)|Gibt den Fortschritt eines **DataControl** -Objekts beim Abrufen von Daten in das **Recordset** -Objekt an.|  
|[Recordset und SourceRecordset (RDS)](./recordset-sourcerecordset-properties-rds.md)|Gibt das **Recordsetobjekt** an, das von einem benutzerdefinierten Geschäftsobjekt zurückgegeben wurde.|  
|[Server (RDS)](./server-property-rds.md)|Gibt den Namen des Internetinformationsdienste (IIS) und das Kommunikationsprotokoll an.|  
|[SortColumn (RDS)](./sortcolumn-property-rds.md)|Gibt an, in welcher Spalte die Datensätze sortiert werden sollen.|  
|[SortDirection (RDS)](./sortdirection-property-rds.md)|Gibt an, ob eine Sortierreihenfolge aufsteigend oder absteigend ist|  
|[SQL (RDS)](./sql-property.md)|Gibt die Abfrage **Zeichenfolge**an, mit der das Recordset abgerufen wird.|  
|[URL (RDS)](./url-property-rds.md)|Gibt eine Zeichenfolge an, die eine relative oder absolute URL enthält.|