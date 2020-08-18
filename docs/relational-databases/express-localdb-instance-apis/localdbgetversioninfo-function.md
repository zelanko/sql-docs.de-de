---
description: LocalDBGetVersionInfo-Funktion
title: Localdbgetversioninfo-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2c4e39c8bf22b4baeccfdd782d48fde7be342f68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88408746"
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo-Funktion
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Gibt Informationen zur angegebenen SQL Server Express-LocalDB-Version zurück, z. B., ob sie vorhanden ist sowie die vollständige LocalDB-Versionsnummer (inklusive Build- und Releasenummer).  
  
 Die Informationen werden in Form einer **Struktur** namens " **localdbversioninfo**" zurückgegeben, die die folgende Definition hat.  
  
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
 *wszversionname*  
 [Eingabe] Der Name der LocalDB-Version.  
  
 *pversioninfo*  
 [Ausgabe] Der Puffer zum Speichern der Informationen zur LocalDB-Version.  
  
 *dwversioninfosize*  
 Der Enthält die Größe des *VERSIONINFO* -Puffers.  
  
## <a name="returns"></a>Rückgabe  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 Die angegebene LocalDB-Version ist nicht vorhanden.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="details"></a>Details  
 Der Grund für die Einführung des **struct** Size-Arguments (*lpversioninfosize*) besteht darin, dass die API die Rückgabe verschiedener Versionen von **localdbversioninfostruct**ermöglicht und somit die vorwärts-und Abwärtskompatibilität effektiv ermöglicht.  
  
 Wenn das **struct** size-Argument (*lpversioninfosize*) mit der Größe einer bekannten Version von **localdbversioninfostruct**übereinstimmt, wird diese Version der **Struktur** zurückgegeben. Andernfalls wird LOCALDB_ERROR_INVALID_PARAMETER zurückgegeben.  
  
 Ein typisches Beispiel für die Verwendung der **localdbgetversioninfo** -API sieht wie folgt aus:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Express LocalDB-Header und Versionsinformationen](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
