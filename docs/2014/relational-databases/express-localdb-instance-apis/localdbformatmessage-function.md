---
title: LocalDBFormatMessage-Funktion | Microsoft-Dokumentation
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
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a48c5d0ef42c2109aebeadf77a6e666e4407093f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246813"
---
# <a name="localdbformatmessage-function"></a>LocalDBFormatMessage-Funktion
  Gibt die lokalisierte Textbeschreibung für den angegebenen SQL Server Express LocalDB-Fehler zurück.  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a>Parameter  
 *hrLocalDB*  
 [Eingabe] Der LocalDB-Fehlercode.  
  
 *dwFlags*  
 [Eingabe] Die Flags, die das Verhalten dieser Funktion angeben.  
  
 Verfügbare Flags:  
  
 LOCALDB_TRUNCATE_ERR_MESSAGE  
 Wenn der Eingabepuffer zu kurz ist, wird die Fehlermeldung abgeschnitten, damit sie in den Puffer passt.  
  
 *dwLanguageId*  
 [Eingabe] Die gewünschte Sprache (LANGID) oder 0, falls die Win32 FormatMessage-Sprachreihenfolge verwendet wird.  
  
 *wszMessage*  
 [Ausgabe] Der Puffer zum Speichern der LocalDB-Fehlermeldung.  
  
 *lpcchMessage*  
 [Eingabe/Ausgabe] Bei Eingabe enthält dieses Objekt die Größe des *wszMessage* -Puffers in Zeichen. Wenn der angegebene Puffer zu klein ist, enthält dieses Objekt bei Ausgabe die erforderliche Puffergröße in Zeichen, einschließlich sämtlicher nachfolgender Nullen. Wenn die Funktion erfolgreich ausgeführt wird, enthält dieses Objekt die Anzahl der Zeichen in der Meldung, ohne nachfolgende Nullen.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_ERROR_CODE](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 Die angeforderte Meldung ist nicht vorhanden.  
  
 [LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 Die Meldung ist in der angeforderten Sprache nicht verfügbar.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Der Eingabepuffer *wszMessage* ist zu kurz. Abschneiden wird nicht angefordert.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  
