---
title: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: b7f138438d522c9da1b7ef74acbaf963e17d6144
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492602"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Microsoft OLE DB-Treiber für SQL Server (Version 18.2.1) Fügt Unterstützung für die UTF-8-Codierung Server hinzu. Informationen über die SQL Server-UTF-8-Unterstützung finden Sie unter:
- [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)
- [UTF-8-Unterstützung](../../../sql-server/what-s-new-in-sql-server-ver15.md#utf-8-support-ctp-23)

## <a name="data-insertion-into-a-utf-8-encoded-char-or-varchar-column"></a>Einfügen von Daten in eine UTF-8 codierte char- oder VARCHAR-Spalte
Wenn Sie einen Puffer Eingabeparameter für das Einfügen zu erstellen, wird der Puffer mithilfe eines Arrays von beschrieben [DBBINDING-Strukturen](https://go.microsoft.com/fwlink/?linkid=2071182). Jede DBBINDING-Struktur einen einzelnen Parameter zu Puffer des Consumers zuordnet, und enthält Informationen wie z. B. Länge und Typ des Datenwerts. Für einen Puffer Eingabeparameter vom Typ char-Zeichen die *wType* von DBBINDING-Struktur sollte auf DBTYPE_STR festgelegt werden. Für einen Eingabeparameter Puffer des Typs WCHAR und die *wType* von DBBINDING-Struktur sollte auf DBTYPE_WSTR festgelegt werden.

Wenn Sie einen Befehl mit Parametern ausführen, erstellt der Treiber Datentypinformationen Parameter an. Wenn der Eingabepuffer-Typ und die Parameterdaten übereinstimmen Vertragstyp, erfolgt keine Konvertierung in den Treiber. Andernfalls konvertiert der Treiber den Eingabeparameter Puffer in den Datentyp des Parameters. Der Parameterdatentyp kann explizit festgelegt werden vom Benutzer durch Aufrufen von [ICommandWithParameters:: SetParameterInfo](https://go.microsoft.com/fwlink/?linkid=2071577). Wenn die Informationen angegeben wird, leitet der Treiber die Datentypinformationen für die Parameter durch (a) Spaltenmetadaten wird vom Server abgerufen, wenn die Anweisung vorbereitet ist, oder (b) versucht, eine standardkonvertierung von dem Datentyp des input-Parameters.

Der Eingabeparameter-Puffer kann auf die Spalte serversortierung vom Treiber oder dem Server je nach den Datentyp für den Eingabepuffer und den Datentyp des Parameters konvertiert werden. Bei der Konvertierung kann Datenverluste auftreten, wenn die Clientcodepage oder die datenbanksortierungs-Codepage nicht alle Zeichen im Eingabepuffer darstellen kann. Die folgende Tabelle beschreibt den Konvertierungsprozess beim Einfügen von Daten in eine UTF-8 Spalte aktiviert:

|Puffer-Datentyp|Parameterdatentyp|Konvertierung|Benutzer Vorsichtsmaßnahme|
|---             |---                |---       |---            |
|DBTYPE_STR|DBTYPE_STR|Server-Konvertierung von Client-Codepage um datenbanksortierungs-Codepage; die serverkonvertierung von datenbanksortierungs-Codepage in Spalte datenbanksortierungs-Codepage.|Stellen Sie sicher, die Client-Codepage, die datenbanksortierungs-Codepage können alle Zeichen in den Eingabedaten darstellen. Z. B. um eine Polnisch Zeichen einzufügen, die Clientcodepage auf 1250 (ANSI Mitteleuropäisch) festgelegt werden, und die Sortierung der Datenbank konnte Polnisch als den Sortierungskennzeichner (z. B. Polish_100_CI_AS_SC) oder UTF-8 aktiviert.|
|DBTYPE_STR|DBTYPE_WSTR|Treiber Konvertierung von Client-Codepage UTF-16-Codierung Server-Konvertierung von UTF-16-Codierung zu Spalte datenbanksortierungs-Codepage.|Stellen Sie sicher, dass die Clientcodepage alle Zeichen in den Eingabedaten darstellen kann. Um ein Polnisch Zeichen einzufügen, konnte die Clientcodepage z. B. um 1250 (ANSI Mitteleuropäisch) festgelegt werden.|
|DBTYPE_WSTR|DBTYPE_STR|Treiber Konvertierung aus UTF-16-Codierung zu datenbanksortierungs-Codepage die serverkonvertierung von datenbanksortierungs-Codepage in Spalte datenbanksortierungs-Codepage.|Stellen Sie sicher, dass die datenbanksortierungs-Codepage alle Zeichen in den Eingabedaten darstellen kann. Z. B. um eine Polnisch Zeichen einzufügen, kann die datenbanksortierungs-Codepage Polnisch als den Sortierungskennzeichner (z. B. Polish_100_CI_AS_SC) oder UTF-8 aktiviert.|
|DBTYPE_WSTR|DBTYPE_WSTR|Die serverkonvertierung von UTF-16 in Spalte datenbanksortierungs-Codepage.|Keine.|

## <a name="data-retrieval-from-a-utf-8-encoded-char-or-varchar-column"></a>Abrufen von Daten aus einer UTF-8 codierte char- oder VARCHAR-Spalte
Wenn Sie einen Puffer für die abgerufenen Daten zu erstellen, wird der Puffer unter Verwendung eines Arrays von beschrieben [DBBINDING-Strukturen](https://go.microsoft.com/fwlink/?linkid=2071182). Jede DBBINDING-Struktur ordnet eine einzelne Spalte in der abgerufenen Zeile. Legen Sie zum Abrufen der Spaltendaten als Zeichen der *wType* der DBBINDING-Struktur, DBTYPE_STR. Legen Sie zum Abrufen der Spaltendaten als WCHAR der *wType* der DBBINDING-Struktur, DBTYPE_WSTR.

Für das Ergebnis Puffer Typindikator DBTYPE_STR konvertiert der Treiber die UTF-8-codierte Daten an den Client-Codierung. Der Benutzer sollten sicherstellen, dass die Client-Codierung aus der UTF-8-Spalte, die andernfalls die Daten darstellen kann Datenverluste auftreten.

Für das Ergebnis Puffer Typindikator DBTYPE_WSTR konvertiert der Treiber die UTF-8-codierte Daten in die UTF-16-Codierung.
  
## <a name="see-also"></a>Weitere Informationen  
[OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[UTF-16-Unterstützung im OLE DB-Treiber für SQL Server (OLE DB)](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
