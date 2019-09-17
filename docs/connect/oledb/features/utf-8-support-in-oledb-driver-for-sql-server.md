---
title: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: fb596365f284a141b5e57bfc8601427fe603d73d
ms.sourcegitcommit: 49f3d12c0a46d98b82513697a77a461340f345e1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70392021"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>UTF-8-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Microsoft OLE DB-Treiber für SQL Server (Version 18.2.1) bietet Unterstützung für die UTF-8-Servercodierung. Informationen zur UTF-8-Unterstützung von SQL Server finden Sie unter:
- [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)
- [UTF-8-Unterstützung](#ctp23)

> [!IMPORTANT]
> Der Microsoft OLE DB-Treiber für SQL Server verwendet die [GetACP-](https://docs.microsoft.com/windows/win32/api/winnls/nf-winnls-getacp) Funktion, um die Codierung des DBTYPE_STR-Eingabe Puffers zu bestimmen. Szenarios, in denen GetACP eine UTF-8-Codierung zurückgibt, werden nicht unterstützt. Wenn der Puffer Unicode-Daten speichern muss, sollte der Puffer Datentyp auf DBTYPE_WSTR (UTF-16-codiert) festgelegt werden.

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

<a name="ctp23"></a>

### <a name="utf-8-support-sql-server-2019-ctp-23"></a>UTF-8-Unterstützung (SQL Server 2019 CTP 2.3)

Mit [!INCLUDE[ss2019](../../../includes/sssqlv15-md.md)] wird die vollständige Unterstützung für die weit verbreitete Zeichencodierung UTF-8 als Import- oder Exportcodierung oder als Sortierung für Textdaten auf Datenbank- oder Spaltenebene eingeführt. UTF-8 ist für die Datentypen `CHAR` und `VARCHAR` zulässig und ist bei der Erstellung oder Änderung einer Objektsortierung in eine Sortierung mit dem Suffix `UTF8` aktiviert.

Beispiel: `LATIN1_GENERAL_100_CI_AS_SC` in `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. Die in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] eingeführte UTF-8-Codierung ist nur für Windows-Sortierungen verfügbar, die Sonderzeichen unterstützen. `NCHAR` und `NVARCHAR` lassen nur die UTF-16-Codierung zu und bleiben unverändert.

Dieses Feature kann abhängig von dem verwendeten Zeichensatz beträchtliche Speichereinsparungen ermöglichen. Die Änderung eines vorhandenen Spaltendatentyps mit ASCII-Zeichen (lateinisch) von `NCHAR(10)` in `CHAR(10)` mit einer UTF-8-fähigen Sortierung führt beispielsweise zu einer Verringerung der Speicheranforderungen um 50 %. Diese Verringerung ist darauf zurückzuführen, dass `NCHAR(10)` 20 Byte für den Speicher erfordert, wohingegen `CHAR(10)` 10 Byte für die gleiche Unicode-Zeichenfolge erfordert.

Weitere Informationen finden Sie unter [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).

**CTP 2.1** unterstützt nun die Auswahl der UTF-8-Sortierung als Standard während des [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)]-Setups.

**CTP 2.2** unterstützt nun die Verwendung von UTF-8-Zeichencodierung mit SQL Server-Replikation.

**CTP 2.3** unterstützt nun die Verwendung von UTF-8-Zeichencodierung mit BIN2-Sortierung (UTF8_BIN2).

## <a name="see-also"></a>Weitere Informationen  
[OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[UTF-16-Unterstützung im OLE DB-Treiber für SQL Server (OLE DB)](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
