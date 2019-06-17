---
title: Informationen in Fehlerschnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60b6b0387aea5475d74c314a10e4fa437fadc005
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62657660"
---
# <a name="information-in-error-interfaces"></a>Informationen in Fehlerschnittstellen
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einige Informationen Fehler- und statusmeldungen in der OLE DB-definierten fehlerschnittstellen **IErrorInfo**, **IErrorRecords**, und **ISQLErrorInfo** .  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **IErrorInfo** -Elementfunktionen wie folgt.  
  
|Memberfunktion|Description|  
|---------------------|-----------------|  
|**GetDescription**|Beschreibende Fehlermeldungs-Zeichenfolge.|  
|**GetGUID**|GUID der Schnittstelle, die den Fehler definiert hat.|  
|**GetHelpContext**|Wird nicht unterstützt. Es wird immer NULL zurückgegeben.|  
|**GetHelpFile**|Wird nicht unterstützt. Gibt immer NULL zurück.|  
|**GetSource**|Zeichenfolge "Microsoft SQL Server Native Client".|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt für Consumer verfügbare **IErrorRecords** -Elementfunktionen wie folgt.  
  
|Memberfunktion|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Füllt eine ERRORINFO-Struktur mit grundlegenden Informationen über einen Fehler aus. Eine ERRORINFO-Struktur enthält Elemente, die den HRESULT-Rückgabewert für den Fehler sowie den Anbieter und die Schnittstelle, für die der Fehler gilt, identifizieren.|  
|**GetCustomErrorObject**|Gibt einen Verweis auf die Schnittstellen **ISQLErrorInfo,** und [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) zurück.|  
|**GetErrorInfo**|Gibt einen Verweis auf eine **IErrorInfo**-Schnittstelle zurück.|  
|**GetErrorParameters**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt keine Parameter zurück, an den Consumer über **GetErrorParameters**.|  
|**GetRecordCount**|Anzahl der verfügbaren Fehlerdatensätze.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **ISQLErrorInfo:: GetSQLInfo** Parameter wie folgt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Gibt einen SQLSTATE-Wert für den Fehler zurück. SQLSTATE-Werte werden in SQL-92, ODBC und ISO SQL sowie der API-Spezifikation definiert. Weder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] noch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert implementierungsabhängige SQLSTATE-Werten.|  
|*plNativeError*|Gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer von **master.dbo.sysmessages** zurück, sofern verfügbar. Systemeigene Fehler verfügbar sind, nach einem erfolgreichen Versuch zum Initialisieren einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbieterdatenquelle. Vor dem Versuch der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt immer 0 (null) zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)  
  
  
