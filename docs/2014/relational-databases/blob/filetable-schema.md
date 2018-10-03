---
title: FileTable-Schema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], table schema
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5c2c2993b4c6ee002c2be0f8bbae28abaa2d87c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088510"
---
# <a name="filetable-schema"></a>FileTable-Schema
  Beschreibt das vordefinierte und feste Schema einer FileTable.  
  
|Name des Dateiattributs|Typ|Größe|Default|Description|Barrierefreiheit für das Dateisystem|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path_locator**|`hierarchyid`|variable|Ein `hierarchyid` , die die Position dieses Elements identifiziert.|Die Position dieses Knotens im hierarchischen FileNamespace.<br /><br /> Primärschlüssel für die Tabelle.|Kann durch Festlegen der Windows-Pfadwerte erstellt und geändert werden.|  
|**stream_id**|**[uniqueidentifier] rowguidcol**||Ein Rückgabewert von der `NEWID()` Funktion.|Eine eindeutige ID für die FILESTREAM-Daten.|Nicht verfügbar.|  
|**file_stream**|`varbinary(max)`<br /><br /> `filestream`|variable|NULL|Enthält die FILESTREAM-Daten.|Nicht verfügbar.|  
|**file_type**|`nvarchar(255)`|variable|NULL.<br /><br /> Durch einen Erstellungs- bzw. Umbenennungsvorgang im Dateisystem wird der Dateierweiterungswert aus dem Namen übernommen.|Stellt den Typ der Datei dar.<br /><br /> Diese Spalte kann als `TYPE COLUMN` verwendet werden, wenn Sie einen Volltextindex erstellen.<br /><br /> **file_type** ist eine persistente berechnete Spalte.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**Name**|`nvarchar(255)`|variable|GUID-Wert.|Der Datei- oder Verzeichnisname.|Kann mit Windows-APIs erstellt oder geändert werden.|  
|**parent_path_locator**|`hierarchyid`|variable|Ein `hierarchyid`, der das Verzeichnis identifiziert, das dieses Element enthält.|Die `hierarchyid` des enthaltenden Verzeichnisses.<br /><br /> **parent_path_locator** ist eine persistente berechnete Spalte.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**cached_file_size**|`bigint`|||Die Größe der FILESTREAM-Daten in Byte.<br /><br /> **cached_file_size** ist eine persistente berechnete Spalte.|Obwohl die zwischengespeicherte Dateigröße automatisch auf dem aktuellen Stand gehalten wird, kann sie unter außergewöhnlichen Umständen möglicherweise nicht synchronisiert sein. Um die genaue Größe zu berechnen, verwenden die `DATALENGTH()` Funktion.|  
|**creation_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit der Erstellung der Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**last_write_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit des letzten Updates der Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**last_access_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit des letzten Zugriffs auf die Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_directory**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Gibt an, ob die Zeile ein Verzeichnis darstellt. Dieser Wert wird automatisch berechnet und kann nicht festgelegt werden.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**is_offline**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für Offlinedatei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_hidden**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für ausgeblendete Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_readonly**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für schreibgeschützte Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_archive**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Archivattribut.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_system**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für Systemdatei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_temporary**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für temporäre Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)  
  
  
