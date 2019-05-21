---
title: SQL Server-Fehlerdetail | Microsoft-Dokumentation
description: SQL Server-Fehlerdetail
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: fc85a2818fcdc72c9450b813a84a4d6d139feae7
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606700"
---
# <a name="sql-server-error-detail"></a>SQL Server-Fehlerdetail
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server definiert die Schnittstelle, anbieterspezifischer Fehler [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). Diese Schnittstelle stellt Details zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlern bereit und ist daher eine nützliche Informationsquelle, wenn Fehler bei der Ausführung von Befehlen oder Rowsetvorgängen auftreten.  
  
 Für den Zugriff auf die **ISQLServerErrorInfo**-Schnittstelle gibt es zwei Möglichkeiten.  
  
 Der Consumer kann **IErrorRecords::GetCustomerErrorObject** aufrufen, um wie im folgenden Codebeispiel gezeigt einen **ISQLServerErrorInfo**-Zeiger zu erhalten. (Es ist nicht nötig, **ISQLErrorInfo** abzurufen.) Sowohl **ISQLErrorInfo** als auch **ISQLServerErrorInfo** sind benutzerdefinierte OLE DB-Fehlerobjekte. Dabei ist **ISQLServerErrorInfo** die Schnittstelle zum Abrufen von Informationen zu Serverfehlern, einschließlich Details wie Prozedurname und Zeilennummern.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Eine andere Möglichkeit, einen **ISQLServerErrorInfo**-Zeiger zu erhalten, besteht im Aufrufen der **QueryInterface**-Methode für einen bereits erhaltenen **ISQLErrorInfo**-Zeiger. Beachten Sie, dass **ISQLServerErrorInfo** eine Obermenge der Informationen enthält, die durch **ISQLErrorInfo** verfügbar sind. Daher ist es sinnvoll, direkt über **GetCustomerErrorObject** zu **ISQLServerErrorInfo** zu gehen.  
  
 Die **ISQLServerErrorInfo**-Schnittstelle macht eine Elementfunktion ([ISQLServerErrorInfo::GetErrorInfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)) verfügbar. Die Funktion gibt einen Zeiger auf eine SSERRORINFO-Struktur und einen Zeiger auf einen Zeichenfolgenpuffer zurück. Beide Zeiger verweisen auf den Arbeitsspeicher, den der Consumer mithilfe der **IMalloc::Free**-Methode freigeben muss.  
  
 SSERRORINFO-Strukturmember werden vom Consumer interpretiert wie folgt.  
  
|Member|Beschreibung|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlermeldung. Identisch mit der Zeichenfolge, die in **IErrorInfo::GetDescription** zurückgegeben wird.|  
|*pwszServer*|Name der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für diese Sitzung.|  
|*pwszProcedure*|Falls zutreffend, der Name der Prozedur, in der der Fehler aufgetreten ist. Andernfalls eine leere Zeichenfolge.|  
|*lNative*|Systemeigene [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlernummer. Identisch mit dem Wert, der im *plNativeError*-Parameter von **ISQLErrorInfo::GetSQLInfo** zurückgegeben wird.|  
|*bState*|Der Status einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*bClass*|Schweregrad einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*wLineNumber*|Falls zutreffend, die Zeilennummer einer gespeicherten Prozedur, in der der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Fehler](../../oledb/ole-db-errors/errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
