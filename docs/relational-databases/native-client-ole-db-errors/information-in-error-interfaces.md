---
title: Informationen in Fehlerschnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 224bf2539da1a9368dc7c204a5d4b4d66f0d964f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43076533"
---
# <a name="information-in-error-interfaces"></a>Informationen in Fehlerschnittstellen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
|**GetCustomErrorObject**|Gibt einen Verweis auf die Schnittstellen **ISQLErrorInfo,** und [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) zurück.|  
|**GetErrorInfo**|Gibt einen Verweis auf eine **IErrorInfo**-Schnittstelle zurück.|  
|**GetErrorParameters**|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt keine Parameter zurück, an den Consumer über **GetErrorParameters**.|  
|**GetRecordCount**|Anzahl der verfügbaren Fehlerdatensätze.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **ISQLErrorInfo:: GetSQLInfo** Parameter wie folgt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Gibt einen SQLSTATE-Wert für den Fehler zurück. SQLSTATE-Werte werden in SQL-92, ODBC und ISO SQL sowie der API-Spezifikation definiert. Weder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] noch die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert implementierungsabhängige SQLSTATE-Werten.|  
|*plNativeError*|Gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer von **master.dbo.sysmessages** zurück, sofern verfügbar. Systemeigene Fehler verfügbar sind, nach einem erfolgreichen Versuch zum Initialisieren einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbieterdatenquelle. Vor dem Versuch der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt immer 0 (null) zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
