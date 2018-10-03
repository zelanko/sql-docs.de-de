---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9131c65236a0efffa19aab2bd10b1fd8e309653b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198380"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)
  Gibt einen Zeiger auf eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter SSERRORINFO-Struktur, enthält die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerdetails.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argumente  
 *ppSSErrorInfo*[out]  
 Ein Zeiger auf eine SSERRORINFO-Struktur. Wenn die Methode fehlschlägt, oder es ist keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Fehler Verknüpfte Informationen der Anbieter keinen Speicher belegen wird, und stellt sicher, dass die *PpSSErrorInfo* Argument ist ein null-Zeiger auf die Ausgabe.  
  
 *ppErrorStrings*[out]  
 Ein Zeiger auf einen Unicode-Zeichenfolgenzeiger. Wenn die Methode fehlschlägt, oder es ist keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Informationen, die mit einem Fehler verknüpft ist, der Anbieter keinen Speicher belegen, und stellt sicher, dass die *PpErrorStrings* Argument ist ein null-Zeiger auf die Ausgabe. Durch die Freigabe des *ppErrorStrings* -Arguments mit der **IMalloc::Free** -Methode werden die drei einzelnen Zeichenfolgenelemente der zurückgegebenen SSERRORINFO-Struktur freigegeben, da der Speicher in einem Block zugeteilt wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_INVALIDARG  
 Entweder das *ppSSErrorInfo* -Argument oder das *ppErrorStrings* -Argument war NULL.  
  
 E_OUTOFMEMORY  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter konnte nicht genügend Arbeitsspeicher zum Ausführen der Anforderung belegt.  
  
## <a name="remarks"></a>Hinweise  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter teilt Arbeitsspeicher für die SSERRORINFO- und die OLECHAR-Zeichenfolgen, die zurückgegeben werden, durch die Zeiger, die vom Consumer übergeben werden. Der Consumer muss diesen Arbeitsspeicher mithilfe der **IMalloc::Free** -Methode freigeben, wenn er keinen Zugriff auf die Fehlerdaten mehr benötigt.  
  
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
|*pwszMessage*|Die Fehlermeldung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Meldung wird durch die **IErrorInfo::GetDescription** -Methode zurückgegeben.|  
|*pwszServer*|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der der Fehler aufgetreten ist.|  
|*pwszProcedure*|Der Name der gespeicherten Prozedur, die den Fehler generiert, wenn der Fehler in einer gespeicherten Prozedur aufgetreten ist; anderenfalls ist es eine leere Zeichenfolge.|  
|*lNative*|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlernummer. Die Fehlernummer ist mit der im *plNativeError* -Parameter der **ISQLErrorInfo::GetSQLInfo** -Methode zurückgegebenen identisch.|  
|*bState*|Der Zustand des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers.|  
|*bClass*|Der Schweregrad des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers.|  
|*wLineNumber*|Falls zutreffend, die Zeile eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozedur, die die Fehlermeldung generiert. Wenn keine Prozedur betroffen ist, lautet der Standardwert 1.|  
  
 Zeiger auf die Strukturverweisadressen in der Zeichenfolge, die im *ppErrorStrings* -Argument zurückgegeben wird  
  
## <a name="see-also"></a>Siehe auch  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
