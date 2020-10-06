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
ms.openlocfilehash: 75124c0fc8d7a0c3c0bb0ea491c84c3673339108
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724351"
---
# <a name="rds-properties"></a>RDS-Eigenschaften
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
|Eigenschaft|BESCHREIBUNG|  
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