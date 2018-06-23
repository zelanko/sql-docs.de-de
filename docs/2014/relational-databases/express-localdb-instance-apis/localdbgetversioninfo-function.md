---
title: LocalDBGetVersionInfo-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03e8e4a07dfed1dc2430f020ad221bfb494eb41f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160432"
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo-Funktion
  Gibt Informationen zur angegebenen SQL Server Express-LocalDB-Version zurück, z. B., ob sie vorhanden ist sowie die vollständige LocalDB-Versionsnummer (inklusive Build- und Releasenummer).  
  
 Die Informationen werden zurückgegeben, in Form von einer `struct` mit dem Namen **LocalDBVersionInfo**, dem weist folgende Definition.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Parameter  
 *wszVersionName*  
 [Eingabe] Der Name der LocalDB-Version.  
  
 *pVersionInfo*  
 [Ausgabe] Der Puffer zum Speichern der Informationen zur LocalDB-Version.  
  
 *dwVersionInfoSize*  
 [Eingabe] Nimmt die Größe der *VersionInfo* Puffer.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 Die angegebene LocalDB-Version ist nicht vorhanden.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="details"></a>Details  
 Der Grund für die Einführung der `struct` -größenargument (*LpVersionInfoSize*) besteht darin, aktivieren die API zurückzugebenden verschiedene Versionen von der **LocalDBVersionInfostruct**effektiv Aktivieren die Aufwärts-und Abwärtskompatibilität.  
  
 Wenn die `struct` -größenargument (*LpVersionInfoSize*) entspricht der Größe einer bekannten Version von der **LocalDBVersionInfostruct**, diese Version von der `struct` zurückgegeben wird. Andernfalls wird LOCALDB_ERROR_INVALID_PARAMETER zurückgegeben.  
  
 Ein typisches Beispiel **LocalDBGetVersionInfo** zur Verwendung der API sieht wie folgt aus:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  