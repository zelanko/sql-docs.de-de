---
title: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: 4a30b233190817faee581106db5c8a18695a00d1
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583013"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Microsoft OLE DB-Treiber für SQL Server (Version 18.2.1) bietet Unterstützung für die UTF-8-Servercodierung. Informationen zur UTF-8-Unterstützung von SQL Server finden Sie unter:
- [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)
- [UTF-8-Unterstützung](../../../sql-server/what-s-new-in-sql-server-ver15.md#utf-8-support-ctp-23)

## <a name="data-insertion-into-a-utf-8-encoded-char-or-varchar-column"></a>Einfügen von Daten in eine UTF-8-codierte CHAR- oder VARCHAR-Spalte
Wenn Sie einen Eingabeparameterpuffer für das Einfügen erstellen, wird der Puffer mithilfe eines Arrays von [DBBINDING-Strukturen](https://go.microsoft.com/fwlink/?linkid=2071182) beschrieben. Jede DBBINDING-Struktur ordnet dem Puffer des Consumers einen einzelnen Parameter zu und enthält Informationen wie z. B. Länge und Typ des Datenwerts. Für einen Eingabeparameterpuffer des Typs CHAR sollte der *wType* der DBBINDING-Struktur auf DBTYPE_STR festgelegt werden. Für einen Eingabeparameterpuffer des Typs WCHAR sollte der *wType* der DBBINDING-Struktur auf DBTYPE_WSTR festgelegt werden.

Beim Ausführen eines Befehls mit Parametern erstellt der Treiber Parameterdatentyp-Informationen. Wenn der Eingabepuffertyp und der Parameterdatentyp übereinstimmen, erfolgt keine Konvertierung im Treiber. Andernfalls konvertiert der Treiber den Eingabeparameterpuffer in den Parameterdatentyp. Der Parameterdatentyp kann vom Benutzer durch Aufrufen von [ICommandWithParameters::SetParameterInfo](https://go.microsoft.com/fwlink/?linkid=2071577) explizit festgelegt werden. Wenn die Informationen nicht angegeben werden, leitet der Treiber die Parameterdatentyp-Informationen ab, indem er (a) Spaltenmetadaten vom Server abruft, wenn die Anweisung vorbereitet wird, oder (b) versucht, eine Standardkonvertierung des Datentyps des Eingabeparameters auszuführen.

Der Eingabeparameterpuffer kann je nach Datentyp des Eingabepuffers und des Parameters vom Treiber oder vom Server in die Serverspaltensortierung konvertiert werden. Bei der Konvertierung können Daten verloren gehen, wenn die Clientcodepage oder die Datenbanksortierungs-Codepage nicht alle Zeichen im Eingabepuffer darstellen kann. In der folgenden Tabelle wird der Konvertierungsprozess beim Einfügen von Daten in eine UTF-8-codierte Spalte beschrieben:

|Pufferdatentyp|Parameterdatentyp|Konvertierung|Vorkehrung|
|---             |---                |---       |---            |
|DBTYPE_STR|DBTYPE_STR|Serverkonvertierung von Clientcodepage in Datenbanksortierungs-Codepage; Serverkonvertierung von Datenbanksortierungs-Codepage in Spaltensortierungs-Codepage.|Stellen Sie sicher, dass alle Zeichen in den Eingabedaten von der Clientcodepage und von der Datenbanksortierungs-Codepage dargestellt werden können. Um beispielsweise ein polnisches Zeichen einzufügen, könnte die Clientcodepage auf 1250 (ANSI Mitteleuropäisch) festgelegt werden, und für die Datenbanksortierung könnte Polnisch als Sortierungskennzeichner verwendet werden (z. B. Polish_100_CI_AS_SC) oder die UTF-8-Codierung aktiviert sein.|
|DBTYPE_STR|DBTYPE_WSTR|Treiberkonvertierung von Clientcodepage in UTF-16-Codierung; Serverkonvertierung von UTF-16-Codierung in Spaltensortierungs-Codepage.|Stellen Sie sicher, dass die Clientcodepage alle Zeichen in den Eingabedaten darstellen kann. Um beispielsweise ein polnisches Zeichen einzufügen, könnte die Clientcodepage auf 1250 (ANSI Mitteleuropäisch) festgelegt werden.|
|DBTYPE_WSTR|DBTYPE_STR|Treiberkonvertierung von UTF-16-Codierung in Datenbanksortierungs-Codepage; Serverkonvertierung von Datenbanksortierungs-Codepage in Spaltensortierungs-Codepage.|Stellen Sie sicher, dass die Datenbanksortierungs-Codepage alle Zeichen in den Eingabedaten darstellen kann. Um beispielsweise ein polnisches Zeichen einzufügen, könnte für die Datenbanksortierungs-Codepage Polnisch als Sortierungskennzeichner verwendet werden (z. B. Polish_100_CI_AS_SC) oder die UTF-8-Codierung aktiviert sein.|
|DBTYPE_WSTR|DBTYPE_WSTR|Serverkonvertierung von UTF-16-Codierung in Spaltensortierungs-Codepage.|Keine.|

## <a name="data-retrieval-from-a-utf-8-encoded-char-or-varchar-column"></a>Abrufen von Daten aus einer UTF-8-codierten CHAR- oder VARCHAR-Spalte
Wenn Sie einen Puffer für abgerufene Daten erstellen, wird der Puffer mithilfe eines Arrays von [DBBINDING-Strukturen](https://go.microsoft.com/fwlink/?linkid=2071182) beschrieben. Jede DBBINDING-Struktur ordnet eine einzelne Spalte in der abgerufenen Zeile zu. Um die Spaltendaten als CHAR abzurufen, legen Sie den *wType* der DBBINDING-Struktur auf DBTYPE_STR fest. Um die Spaltendaten als WCHAR abzurufen, legen Sie den *wType* der DBBINDING-Struktur auf DBTYPE_WSTR fest.

Für den Puffertypindikator DBTYPE_STR konvertiert der Treiber die UTF-8-codierten Daten in die Clientcodierung. Der Benutzer sollte sicherstellen, dass die Clientcodierung die Daten aus der UTF-8-codierten Spalte darstellen kann. Andernfalls können Daten verloren gehen.

Für den Puffertypindikator DBTYPE_WSTR konvertiert der Treiber die UTF-8-codierten Daten in die UTF-16-Codierung.
  
## <a name="see-also"></a>Weitere Informationen  
[OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[UTF-16-Unterstützung im OLE DB-Treiber für SQL Server (OLE DB)](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
