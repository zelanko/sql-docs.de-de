---
description: RDS-Methoden
title: RDS-Methoden | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- RDS methods [ADO]
- methods [ADO], RDS
ms.assetid: c2c6af1a-3c44-4c9d-ad33-b381552c71af
author: rothja
ms.author: jroth
ms.openlocfilehash: f65c669a12fce6b78572e2bacd3152cdb5793216
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724361"
---
# <a name="rds-methods"></a>RDS-Methoden
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
|Methode|BESCHREIBUNG|  
|-|-|  
|[Abbrechen (RDS)](./cancel-method-rds.md)|Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.|  
|[CancelUpdate (RDS)](./cancelupdate-method-rds.md)|Bricht alle Änderungen ab, die an der aktuellen oder neuen Zeile eines **Recordset** -Objekts vorgenommen wurden.|  
|[ConvertTo String (RDS)](./converttostring-method-rds.md)|Konvertiert ein **Recordset** in eine MIME-Zeichenfolge, die die Recordsetdaten darstellt.|  
|["Kreateobject" (RDS)](./createobject-method-rds.md)|Erstellt den Proxy für das Ziel Geschäftsobjekt und gibt einen Zeiger darauf zurück.|  
|["Kreaterecordset" (RDS)](./createrecordset-method-rds.md)|Erstellt ein leeres, nicht verbundenes **Recordset**.|  
|[Execute-Methode (RDS)](./execute-method-rds.md)|Führen Sie die Anforderung aus, und erstellen Sie ein erweitertes Datenrowset (für die Verwendung mit ADO 2,5 und höher).|  
|[Execute21-Methode (RDS)](./execute21-method-rds.md)|Führen Sie die Anforderung aus, und erstellen Sie ein erweitertes Datenrowset (für die Verwendung mit ADO 2,1).|  
|[InvokeService (RDS)](./invokeservice-rds.md)|Gibt einen Zeiger auf die angeforderte Schnittstelle für eine leistungsfähigere Version des-Objekts zurück.|  
|["Muvefirst", "muvelast", "muvenext" (RDS)](./movefirst-movelast-movenext-and-moveprevious-methods-rds.md)|Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen **Recordset** -Objekt.|  
|[Abfrage (RDS)](./query-method-rds.md)|Verwendet eine gültige SQL-Abfrage **Zeichenfolge**zum Zurückgeben eines Recordsets.|  
|[Aktualisieren (RDS)](./refresh-method-rds.md)|Fragt die in der **Connect** -Eigenschaft angegebene Datenquelle ab und aktualisiert die Abfrageergebnisse.|  
|[Zurücksetzen (RDS)](./reset-method-rds.md)|Führt die Sortierung oder den Filter für ein Client seitiges **Recordset**basierend auf den angegebenen Sortier-und Filtereigenschaften aus.|  
|[SubmitChanges (RDS)](./submitchanges-method-rds.md)|Übermittelt ausstehende Änderungen des lokal zwischengespeicherten und aktualisierbaren **Recordsets** an die Datenquelle, die in der **Connect** -Eigenschaft angegeben ist.|  
|[Synchronize-Methode (RDS)](./synchronize-method-rds.md)|Synchronisieren Sie das angegebene Recordset mit der Datenbank, die durch die Verbindungs Zeichenfolge angegeben wird (zur Verwendung mit ADO 2,5 und höher).|  
|[Synchronize21-Methode (RDS)](./synchronize21-method-rds.md)|Synchronisieren Sie das angegebene Recordset mit der Datenbank, die durch die Verbindungs Zeichenfolge angegeben wird (zur Verwendung mit ADO 2,1).|