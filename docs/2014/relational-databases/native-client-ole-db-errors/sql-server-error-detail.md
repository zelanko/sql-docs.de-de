---
title: SQL Server-Fehlerdetail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbbf2365603998edabe58a01de840f2969a8c263
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150123"
---
# <a name="sql-server-error-detail"></a>SQL Server-Fehlerdetail
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert die Schnittstelle anbieterspezifischer Fehler [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). Diese Schnittstelle stellt Details zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern bereit und ist daher eine nützliche Informationsquelle, wenn Fehler bei der Ausführung von Befehlen oder Rowsetvorgängen auftreten.  
  
 Es gibt zwei Möglichkeiten, erhalten Zugriff auf **ISQLServerErrorInfo** Schnittstelle.  
  
 Der Consumer kann aufgerufen werden **IErrorRecords:: Getcustomererrorobject** zum Abrufen einer **ISQLServerErrorInfo** -Zeiger ist, wie im folgenden Codebeispiel gezeigt. (Besteht keine Notwendigkeit zum Abrufen **ISQLErrorInfo.**) Beide **ISQLErrorInfo** und **ISQLServerErrorInfo** sind benutzerdefinierte OLE DB-Fehlerobjekte mit **ISQLServerErrorInfo** wird die Schnittstelle zum Abrufen von Informationen Serverfehlern einschließlich Details wie Prozedurname und Zeilennummern Zeilennummern.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Eine weitere Möglichkeit zum Abrufen einer **ISQLServerErrorInfo** Zeiger besteht im Aufrufen der **QueryInterface** Methode für einen bereits erhaltenen **ISQLErrorInfo** Zeiger. Beachten Sie, dass, weil **ISQLServerErrorInfo** enthält eine Obermenge der verfügbaren Informationen von **ISQLErrorInfo**, es ist sinnvoll, direkt **ISQLServerErrorInfo**über **ISQLServerErrorInfo**.  
  
 Die **ISQLServerErrorInfo** Schnittstelle macht eine Memberfunktion, [ISQLServerErrorInfo:: GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). Die Funktion gibt einen Zeiger auf eine SSERRORINFO-Struktur und einen Zeiger auf einen Zeichenfolgenpuffer zurück. Beide Zeiger verweisen auf den Arbeitsspeicher, die der Consumer muss Aufheben der Zuordnung mithilfe der **IMalloc:: Free** Methode.  
  
 SSERRORINFO-Strukturmember werden vom Consumer interpretiert wie folgt.  
  
|Member|Description|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung. Identisch mit der Zeichenfolge zurückgegeben, die **IErrorInfo:: GetDescription**.|  
|*pwszServer*|Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für diese Sitzung.|  
|*pwszProcedure*|Falls zutreffend, der Name der Prozedur, in der der Fehler aufgetreten ist. Andernfalls eine leere Zeichenfolge.|  
|*lNative*|Systemeigene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer. Identisch mit den zurückgegebenen Wert der *PlNativeError* Parameter **ISQLErrorInfo:: GetSQLInfo**.|  
|*bState*|Der Status einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*bClass*|Schweregrad einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlermeldung.|  
|*wLineNumber*|Falls zutreffend, die Zeilennummer einer gespeicherten Prozedur, in der der Fehler aufgetreten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
