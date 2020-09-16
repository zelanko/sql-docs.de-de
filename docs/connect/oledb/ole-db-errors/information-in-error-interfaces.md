---
title: Informationen in Fehlerschnittstellen
description: Der OLE DB-Treiber für SQL Server stellt einige Fehler- und Statusinformationen in den OLE DB-definierten Fehlerschnittstellen „IErrorInfo“, „IErrorRecords“ und „ISQLErrorInfo“ bereit.
ms.custom: ''
ms.date: 05/06/2020
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 023926ff67c85dcf8d95499b8281853bf7b3b1f3
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860008"
---
# <a name="information-in-error-interfaces"></a>Informationen in Fehlerschnittstellen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server stellt einige Fehler- und Statusinformationen in den OLE DB-definierten Fehlerschnittstellen **IErrorInfo**, **IErrorRecords** und **ISQLErrorInfo** bereit.  
  
 Der OLE DB-Treiber für SQL Server unterstützt **IErrorInfo**-Elementfunktionen wie folgt.  
  
|Memberfunktion|BESCHREIBUNG|  
|---------------------|-----------------|  
|**GetDescription**|Beschreibende Fehlermeldungs-Zeichenfolge.|  
|**GetGUID**|GUID der Schnittstelle, die den Fehler definiert hat.|  
|**GetHelpContext**|Wird nicht unterstützt. Es wird immer NULL zurückgegeben.|  
|**GetHelpFile**|Wird nicht unterstützt. Gibt immer NULL zurück.|  
|**GetSource**|Zeichenfolge „Microsoft OLE DB-Treiber für SQL Server“.|  
  
 Der OLE DB-Treiber für SQL Server unterstützt für Consumer verfügbare **IErrorRecords**-Elementfunktionen wie folgt.  
  
|Memberfunktion|BESCHREIBUNG|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Füllt eine ERRORINFO-Struktur mit grundlegenden Informationen über einen Fehler aus. Eine ERRORINFO-Struktur enthält Elemente, die den HRESULT-Rückgabewert für den Fehler sowie den Anbieter und die Schnittstelle, für die der Fehler gilt, identifizieren.|  
|**GetCustomErrorObject**|Gibt einen Verweis auf die Schnittstellen **ISQLErrorInfo,** und [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15) zurück.|  
|**GetErrorInfo**|Gibt einen Verweis auf eine **IErrorInfo**-Schnittstelle zurück.|  
|**GetErrorParameters**|Der OLE DB-Treiber für SQL Server gibt keine Parameter über **GetErrorParameters** an den Consumer zurück.|  
|**GetRecordCount**|Anzahl der verfügbaren Fehlerdatensätze.|  
  
 Der OLE DB-Treiber für SQL Server unterstützt **ISQLErrorInfo::GetSQLInfo**-Parameter wie folgt.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*pbstrSQLState*|Gibt einen SQLSTATE-Wert für den Fehler zurück. SQLSTATE-Werte werden in SQL-92, ODBC und ISO SQL sowie der API-Spezifikation definiert. Weder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] noch der OLE DB-Treiber für SQL Server definieren implementierungsabhängige SQLSTATE-Werte.|  
|*plNativeError*|Gibt die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlernummer von **master.dbo.sysmessages** zurück, sofern verfügbar. Nach einem erfolgreichen Versuch, eine Datenquelle für den OLE DB-Treiber für SQL Server zu initialisieren, sind native Fehler verfügbar. Vor dem Versuch gibt der OLE DB-Treiber für SQL Server immer 0 (null) zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler](../../oledb/ole-db-errors/errors.md)  
  
  
