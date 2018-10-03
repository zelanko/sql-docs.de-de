---
title: Informationen in Fehlerschnittstellen | Microsoft-Dokumentation
description: Informationen in Fehlerschnittstellen
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4ca0d4337a4377f1c61d118db7852b195dc279e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684408"
---
# <a name="information-in-error-interfaces"></a>Informationen in Fehlerschnittstellen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server stellt einige Fehler- und Statusinformationen in den OLE DB-definierten Fehlerschnittstellen **IErrorInfo**, **IErrorRecords** und **ISQLErrorInfo** bereit.  
  
 Der OLE DB-Treiber für SQL Server unterstützt **IErrorInfo** -Elementfunktionen wie folgt.  
  
|Memberfunktion|und Beschreibung|  
|---------------------|-----------------|  
|**GetDescription**|Beschreibende Fehlermeldungs-Zeichenfolge.|  
|**GetGUID**|GUID der Schnittstelle, die den Fehler definiert hat.|  
|**GetHelpContext**|Wird nicht unterstützt. Es wird immer NULL zurückgegeben.|  
|**GetHelpFile**|Wird nicht unterstützt. Gibt immer NULL zurück.|  
|**GetSource**|Zeichenfolge „Microsoft OLE DB-Treiber für SQL Server“.|  
  
 Der OLE DB-Treiber für SQL Server unterstützt für Consumer verfügbare **IErrorRecords** -Elementfunktionen wie folgt.  
  
|Memberfunktion|und Beschreibung|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Füllt eine ERRORINFO-Struktur mit grundlegenden Informationen über einen Fehler aus. Eine ERRORINFO-Struktur enthält Elemente, die den HRESULT-Rückgabewert für den Fehler sowie den Anbieter und die Schnittstelle, für die der Fehler gilt, identifizieren.|  
|**GetCustomErrorObject**|Gibt einen Verweis auf die Schnittstellen **ISQLErrorInfo,** und [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) zurück.|  
|**GetErrorInfo**|Gibt einen Verweis auf eine **IErrorInfo**-Schnittstelle zurück.|  
|**GetErrorParameters**|Der OLE DB-Treiber für SQL Server gibt keine Parameter zurück, an den Consumer über **GetErrorParameters**.|  
|**GetRecordCount**|Anzahl der verfügbaren Fehlerdatensätze.|  
  
 Der OLE DB-Treiber für SQL Server unterstützt **ISQLErrorInfo:: GetSQLInfo** Parameter wie folgt.  
  
|Parameter|und Beschreibung|  
|---------------|-----------------|  
|*pbstrSQLState*|Gibt einen SQLSTATE-Wert für den Fehler zurück. SQLSTATE-Werte werden in SQL-92, ODBC und ISO SQL sowie der API-Spezifikation definiert. Weder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] noch der OLE DB-Treiber für SQL Server definierte implementierungsabhängige SQLSTATE-Werten.|  
|*plNativeError*|Gibt die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlernummer von **master.dbo.sysmessages** zurück, sofern verfügbar. Systemeigene Fehler sind nach einem erfolgreichen Versuch zur Initialisierung von einer OLE DB-Treiber für SQL Server-Datenquelle verfügbar. Vor dem Versuch gibt der OLE DB-Treiber für SQL Server immer 0 (null) zurück.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
