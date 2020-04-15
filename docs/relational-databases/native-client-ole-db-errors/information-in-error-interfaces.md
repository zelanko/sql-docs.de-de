---
title: Informationen in Fehlerschnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a19a2189aa28bb5ebf50a0533ed4bfb30b52deea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306098"
---
# <a name="information-in-error-interfaces"></a>Informationen in Fehlerschnittstellen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter meldet einige Fehler- und Statusinformationen in den OLE DB-definierten Fehlerschnittstellen **IErrorInfo**, **IErrorRecords**und **ISQLErrorInfo**.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt **IErrorInfo-Memberfunktionen** wie folgt.  
  
|Memberfunktion|Beschreibung|  
|---------------------|-----------------|  
|**GetDescription**|Beschreibende Fehlermeldungs-Zeichenfolge.|  
|**GetGUID**|GUID der Schnittstelle, die den Fehler definiert hat.|  
|**GetHelpContext**|Wird nicht unterstützt. Es wird immer NULL zurückgegeben.|  
|**GetHelpFile**|Wird nicht unterstützt. Gibt immer NULL zurück.|  
|**GetSource**|Zeichenfolge "Microsoft SQL Server Native Client".|  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt die vom Verbraucher verfügbaren **IErrorRecords-Memberfunktionen** wie folgt.  
  
|Memberfunktion|Beschreibung|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Füllt eine ERRORINFO-Struktur mit grundlegenden Informationen über einen Fehler aus. Eine ERRORINFO-Struktur enthält Elemente, die den HRESULT-Rückgabewert für den Fehler sowie den Anbieter und die Schnittstelle, für die der Fehler gilt, identifizieren.|  
|**GetCustomErrorObject**|Gibt einen Verweis auf die Schnittstellen **ISQLErrorInfo,** und [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) zurück.|  
|**GetErrorInfo**|Gibt einen Verweis auf eine **IErrorInfo**-Schnittstelle zurück.|  
|**GetErrorParameters**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter gibt über **GetErrorParameters**keine Parameter an den Consumer zurück.|  
|**GetRecordCount**|Anzahl der verfügbaren Fehlerdatensätze.|  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt die Parameter **ISQLErrorInfo::GetSQLInfo** wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*pbstrSQLState*|Gibt einen SQLSTATE-Wert für den Fehler zurück. SQLSTATE-Werte werden in SQL-92, ODBC und ISO SQL sowie der API-Spezifikation definiert. Weder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der native Client-OLE-DB-Anbieter definierte implementierungsspezifische SQLSTATE-Werte.|  
|*plNativeError*|Gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer von **master.dbo.sysmessages** zurück, sofern verfügbar. Native Fehler sind nach einem erfolgreichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versuch verfügbar, eine Native Client OLE DB-Anbieterdatenquelle zu initialisieren. Vor dem Versuch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client OLE DB-Anbieter immer Null zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Errors](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
