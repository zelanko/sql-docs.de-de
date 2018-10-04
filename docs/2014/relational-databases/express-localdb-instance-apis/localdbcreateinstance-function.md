---
title: LocalDBCreateInstance-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4a34fff85c1b5c4277c17f880756eab2c7bba268
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227280"
---
# <a name="localdbcreateinstance-function"></a>LocalDBCreateInstance-Funktion
  Erstellt eine neue SQL Server Express LocalDB-Instanz.  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a>Parameter  
 *wszVersion*  
 [Eingabe] Die LocalDB-Version, z. B. 11.0 oder 11.0.1094.2.  
  
 *pInstanceName*  
 [Eingabe] Der Name für die zu erstellende LocalDB-Instanz.  
  
 *dwFlags*  
 [Eingabe] Zur künftigen Verwendung reserviert. Muss derzeit auf 0 festgelegt sein.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Der angegebene Instanzname ist ungültig.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Der Pfad, unter dem die Instanz gespeichert werden soll, ist länger als MAX_PATH.  
  
 [LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 Die angegebene Instanz ist bereits vorhanden, aber ihre Version ist niedriger als angefordert.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 Die angegebene Version ist nicht verfügbar.  
  
 [LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 Die angegebene Patchebene ist nicht installiert.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 Ein Ordner kann nicht unter %userprofile% erstellt werden.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Ein Benutzerprofilordner kann nicht abgerufen werden.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Auf einen Instanzordner kann nicht zugegriffen werden.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Auf eine Instanzregistrierung kann nicht zugegriffen werden.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 Eine Instanzregistrierung kann nicht bearbeitet werden.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Ein SQL Server-Prozess wird gestartet, der SQL Server-Start ist jedoch fehlgeschlagen.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Eine Instanzkonfiguration ist beschädigt.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine vollständig funktionierende LocalDB-Instanz mit dem angegebenen Namen bereits vorhanden ist und ihre Version der angeforderten entspricht oder höher ist, ist das Ergebnis S_OK.  
  
 In Fällen wird eine vorhandene Instanz beschädigt, schlagen nachfolgende Aufrufe der `LocalDBCreateInstance` API-Methode fehl. Beschädigte Instanzen müssen manuell korrigiert oder explizit gelöscht werden, bevor sie wieder verwendet werden können.  
  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  
