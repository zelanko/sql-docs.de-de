---
title: LocalDBGetVersions-Funktion | Microsoft Docs
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
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 95117c20b67777f7202ee823c17ba8775843295e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047589"
---
# <a name="localdbgetversions-function"></a>LocalDBGetVersions-Funktion
  Gibt alle auf dem Computer verfügbaren SQL Server Express LocalDB-Versionen zurück.  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a>Parameter  
 *pVersionNames*  
 [Ausgabe] Enthält Namen der LocalDB-Versionen, die auf der Arbeitsstation des Benutzers verfügbar sind.  
  
 *lpdwNumberOfVersions*  
 [Eingabe/Ausgabe] Enthält bei Eingabe die Anzahl der Slots für Versionen im *pVersionNames* -Puffer.   
Enthält bei Ausgabe die Anzahl der vorhandenen LocalDB-Versionen.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Der Eingabepuffer ist zu kurz. Abschneiden wurde nicht angefordert.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  