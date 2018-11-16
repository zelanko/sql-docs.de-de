---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c51c41d80ac3d24f0d63c31b9354941e93499d1a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678040"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Gibt einen Zeiger auf eine SSERRORINFO-Struktur des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieters zurück, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerdetails enthält.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE Datenbank-Anbieter definiert die **ISQLServerErrorInfo** -Fehlerschnittstelle. Diese Schnittstelle gibt Details zu einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler zurück, einschließlich seines Schweregrads und Status.  

  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argumente  
 *ppSSErrorInfo*[out]  
 Ein Zeiger auf eine SSERRORINFO-Struktur. Wenn die Methode fehlschlägt oder dem Fehler keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Informationen zugeordnet sind, teilt der Anbieter keinen Speicher zu und stellt sicher, dass das *ppSSErrorInfo* -Argument bei der Ausgabe ein NULL-Zeiger ist.  
  
 *ppErrorStrings*[out]  
 Ein Zeiger auf einen Unicode-Zeichenfolgenzeiger. Wenn die Methode fehlschlägt oder dem Fehler keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Informationen zugeordnet sind, teilt der Anbieter keinen Speicher zu und stellt sicher, dass das *ppErrorStrings* -Argument bei der Ausgabe ein NULL-Zeiger ist. Durch die Freigabe des *ppErrorStrings* -Arguments mit der **IMalloc::Free** -Methode werden die drei einzelnen Zeichenfolgenelemente der zurückgegebenen SSERRORINFO-Struktur freigegeben, da der Speicher in einem Block zugeteilt wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_INVALIDARG  
 Entweder das *ppSSErrorInfo* -Argument oder das *ppErrorStrings* -Argument war NULL.  
  
 E_OUTOFMEMORY  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter konnte nicht genügend Arbeitsspeicher zuteilen, um die Anforderung zu erfüllen.  
  
## <a name="remarks"></a>Hinweise  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter teilt Arbeitsspeicher für die SSERRORINFO- und die OLECHAR-Zeichenfolgen zu, die durch die Zeiger zurückgegeben werden, die vom Consumer übergeben werden. Der Consumer muss diesen Arbeitsspeicher mithilfe der **IMalloc::Free** -Methode freigeben, wenn er keinen Zugriff auf die Fehlerdaten mehr benötigt.  
  
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
|*pwszServer*|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], auf der der Fehler aufgetreten ist|  
|*pwszProcedure*|Der Name der gespeicherten Prozedur, die den Fehler generiert, wenn der Fehler in einer gespeicherten Prozedur aufgetreten ist; anderenfalls ist es eine leere Zeichenfolge.|  
|*lNative*|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlernummer. Die Fehlernummer ist mit der im *plNativeError* -Parameter der **ISQLErrorInfo::GetSQLInfo** -Methode zurückgegebenen identisch.|  
|*bState*|Der Zustand des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlers.|  
|*bClass*|Der Schweregrad des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlers.|  
|*wLineNumber*|Das ist gegebenenfalls die Zeile einer gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur, die die Fehlermeldung generiert hat. Wenn keine Prozedur betroffen ist, lautet der Standardwert 1.|  
  
 Zeiger auf die Strukturverweisadressen in der Zeichenfolge, die im *ppErrorStrings* -Argument zurückgegeben wird  
  
## <a name="see-also"></a>Siehe auch  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
