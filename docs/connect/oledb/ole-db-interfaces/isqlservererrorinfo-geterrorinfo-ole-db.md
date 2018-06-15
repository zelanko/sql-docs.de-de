---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Microsoft Docs'
description: "'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)"
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 085b171b9987e8546560550fbf9a71eadbf8de31
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305749"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Gibt einen Zeiger auf einen OLE DB-Treiber für SQL Server-SSERRORINFO Struktur mit den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fehlerdetails.  
  
 Der OLE DB-Treiber für SQL Server definiert die **ISQLServerErrorInfo** fehlerschnittstelle. Diese Schnittstelle gibt Details zu einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fehler, einschließlich seines Schweregrads und Status.  

  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argumente  
 *ppSSErrorInfo*[out]  
 Ein Zeiger auf eine SSERRORINFO-Struktur. Wenn die Methode fehlschlägt, oder es ist keine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem Fehler Verknüpfte Informationen der Anbieter nicht Speicher und stellt sicher, dass die *PpSSErrorInfo* Argument ist ein null-Zeiger in der Ausgabe.  
  
 *ppErrorStrings*[out]  
 Ein Zeiger auf einen Unicode-Zeichenfolgenzeiger. Wenn die Methode fehlschlägt, oder es ist keine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Informationen, die mit einem Fehler verknüpft sind, der Anbieter nicht Speicher und stellt sicher, dass die *PpErrorStrings* Argument ist ein null-Zeiger in der Ausgabe. Durch die Freigabe des *ppErrorStrings* -Arguments mit der **IMalloc::Free** -Methode werden die drei einzelnen Zeichenfolgenelemente der zurückgegebenen SSERRORINFO-Struktur freigegeben, da der Speicher in einem Block zugeteilt wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_INVALIDARG  
 Entweder das *ppSSErrorInfo* -Argument oder das *ppErrorStrings* -Argument war NULL.  
  
 E_OUTOFMEMORY  
 Der OLE DB-Treiber für SQL Server konnte nicht genügend Arbeitsspeicher zum Ausführen der Anforderung zuordnen.  
  
## <a name="remarks"></a>Hinweise  
 Der OLE DB-Treiber für SQL Server belegt Speicher für die SSERRORINFO- und die OLECHAR-Zeichenfolgen, die durch die Zeiger, die vom Consumer übergeben werden zurückgegeben. Der Consumer muss diesen Arbeitsspeicher mithilfe der **IMalloc::Free** -Methode freigeben, wenn er keinen Zugriff auf die Fehlerdaten mehr benötigt.  
  
 Die SSERRORINFO-Struktur ist folgendermaßen definiert:  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|Member|Description|  
|------------|-----------------|  
|*pwszMessage*|Die Fehlermeldung aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Die Meldung wird durch die **IErrorInfo::GetDescription** -Methode zurückgegeben.|  
|*pwszServer*|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf dem der Fehler auftrat.|  
|*pwszProcedure*|Der Name der gespeicherten Prozedur, die den Fehler generiert, wenn der Fehler in einer gespeicherten Prozedur aufgetreten ist; anderenfalls ist es eine leere Zeichenfolge.|  
|*lNative*|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fehlernummer. Die Fehlernummer ist mit der im *plNativeError* -Parameter der **ISQLErrorInfo::GetSQLInfo** -Methode zurückgegebenen identisch.|  
|*bState*|Der Zustand des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlers.|  
|*bClass*|Der Schweregrad des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlers.|  
|*wLineNumber*|Gegebenenfalls die Zeile eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gespeicherten Prozedur, die die Fehlermeldung generiert hat. Wenn keine Prozedur betroffen ist, lautet der Standardwert 1.|  
  
 Zeiger auf die Strukturverweisadressen in der Zeichenfolge, die im *ppErrorStrings* -Argument zurückgegeben wird  
  
## <a name="see-also"></a>Siehe auch  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
