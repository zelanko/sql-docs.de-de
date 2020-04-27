---
title: SQL Server-Fehlerdetail | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c7535e4579204834fc8024b7c37c46675320b8f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63156395"
---
# <a name="sql-server-error-detail"></a>SQL Server-Fehlerdetail
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert die anbieterspezifische Fehler Schnittstelle [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). Diese Schnittstelle stellt Details zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern bereit und ist daher eine nützliche Informationsquelle, wenn Fehler bei der Ausführung von Befehlen oder Rowsetvorgängen auftreten.  
  
 Für den Zugriff auf die **ISQLServerErrorInfo**-Schnittstelle gibt es zwei Möglichkeiten.  
  
 Der Consumer kann **IErrorRecords::GetCustomerErrorObject** aufrufen, um wie im folgenden Codebeispiel gezeigt einen **ISQLServerErrorInfo**-Zeiger zu erhalten. (Es ist nicht nötig, **ISQLErrorInfo** abzurufen.) Sowohl **ISQLErrorInfo** als auch **ISQLServerErrorInfo** sind benutzerdefinierte OLE DB-Fehlerobjekte. Dabei ist **ISQLServerErrorInfo** die Schnittstelle zum Abrufen von Informationen zu Serverfehlern, einschließlich Details wie Prozedurname und Zeilennummern.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Eine andere Möglichkeit, einen **ISQLServerErrorInfo**-Zeiger zu erhalten, besteht im Aufrufen der **QueryInterface**-Methode für einen bereits erhaltenen **ISQLErrorInfo**-Zeiger. Beachten Sie, dass **ISQLServerErrorInfo** eine Obermenge der Informationen enthält, die durch **ISQLErrorInfo** verfügbar sind. Daher ist es sinnvoll, direkt über **GetCustomerErrorObject** zu **ISQLServerErrorInfo** zu gehen.  
  
 Die **ISQLServerErrorInfo**-Schnittstelle macht eine Elementfunktion ([ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)) verfügbar. Die Funktion gibt einen Zeiger auf eine SSERRORINFO-Struktur und einen Zeiger auf einen Zeichenfolgenpuffer zurück. Beide Zeiger verweisen auf den Arbeitsspeicher, den der Consumer mithilfe der **IMalloc::Free**-Methode freigeben muss.  
  
 SSERRORINFO-Strukturmember werden vom Consumer interpretiert wie folgt.  
  
|Member|Beschreibung|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung. Identisch mit der Zeichenfolge, die in **IErrorInfo::GetDescription** zurückgegeben wird.|  
|*pwszServer*|Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für diese Sitzung.|  
|*pwszProcedure*|Falls zutreffend, der Name der Prozedur, in der der Fehler aufgetreten ist. Andernfalls eine leere Zeichenfolge.|  
|*lNative*|Systemeigene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer. Identisch mit dem Wert, der im *plNativeError*-Parameter von **ISQLErrorInfo::GetSQLInfo** zurückgegeben wird.|  
|*bState*|Der Status einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*bClass*|Schweregrad einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*wLineNumber*|Falls zutreffend, die Zeilennummer einer gespeicherten Prozedur, in der der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mern](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
