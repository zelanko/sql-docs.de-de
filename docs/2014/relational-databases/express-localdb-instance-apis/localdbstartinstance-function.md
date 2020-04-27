---
title: Localdbstartinstance-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ad86f5989fe9ff90132637d062b708423f23eef1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63131493"
---
# <a name="localdbstartinstance-function"></a>LocalDBStartInstance-Funktion
  Startet die angegebene SQL Server Express LocalDB-Instanz.  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a>Parameter  
 *pinstancename*  
 [Eingabe] Der Name der LocalDB-Instanz, die gestartet werden soll.  
  
 *dwFlags*  
 [Eingabe] Zur künftigen Verwendung reserviert. Muss derzeit auf 0 festgelegt sein.  
  
 *wszSqlConnection*  
 [Ausgabe] Der Puffer zum Speichern der Verbindungszeichenfolge in der LocalDB-Instanz.  
  
 *lpcchSqlConnection*  
 [Eingabe/Ausgabe] Bei Eingabe enthält dieses Objekt die Größe des *wszSqlConnection* -Puffers in Zeichen, einschließlich sämtlicher nachfolgender Nullen. Wenn der angegebene Puffer zu klein ist, enthält dieses Objekt bei Ausgabe die erforderliche Puffergröße in Zeichen, einschließlich sämtlicher nachfolgender Nullen.  
  
## <a name="returns"></a>Rückgabe  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Der angegebene Instanzname ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 Die Instanz ist nicht vorhanden.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Der angegebene Puffer *wszSqlConnection* ist zu klein.  
  
 [LOCALDB_ERROR_WAIT_TIMEOUT](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 Beim versuchten Abrufen der Synchronisierungssperren ist ein Timeout aufgetreten.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Der Pfad, unter dem die Instanz gespeichert werden soll, ist länger als MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Ein Benutzerprofilordner kann nicht abgerufen werden.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Auf einen Instanzordner kann nicht zugegriffen werden.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Auf eine Instanzregistrierung kann nicht zugegriffen werden.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 Eine Instanzregistrierung kann nicht bearbeitet werden.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS](../express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 Ein Prozess für SQL Server kann nicht erstellt werden.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Ein SQL Server-Prozess wurde gestartet, der SQL Server-Start ist jedoch fehlgeschlagen.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Eine Instanzkonfiguration war beschädigt.  
  
 [LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED](../express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 Kann keine automatische Instanz erstellen. Fehlerdetails finden Sie im Windows-Anwendungsereignisprotokoll.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="details"></a>Details  
 Das Verbindungspufferargument (*wszSqlConnection*) und das Verbindungspuffergrößen-Argument (*lpcchSqlConnection*) sind optional. In der folgenden Tabelle werden Optionen zum Verwenden dieser Argumente und ihrer Ergebnisse angezeigt.  
  
|Buffer|Puffergröße|Sinn|Aktion|  
|------------|-----------------|---------------|------------|  
|NULL|NULL|Der Benutzer möchte die Instanz starten und benötigt keinen Pipenamen.|Startet eine Instanz (keine Piperückgabe und keine erforderliche Puffergrößenrückgabe).|  
|NULL|Anzahl|Benutzer fragt nach der Ausgabepuffergröße. (Im nächsten Aufruf bittet der Benutzer wahrscheinlich um einen tatsächlichen Start.)|Gibt eine erforderliche Puffergröße (kein Start und keine Piperückgabe) zurück. Ergebnis ist S_OK.|  
|Anzahl|NULL|Nicht zulässig; falsche Eingabe.|Das zurückgegebene Ergebnis ist LOCALDB_ERROR_INVALID_PARAMETER.|  
|Anzahl|Anzahl|Der Benutzer möchte die Instanz starten und benötigt den Pipenamen, zu dem nach dem Start eine Verbindung hergestellt wird.|Überprüft die Puffergröße, startet die Instanz und gibt den Pipenamen im Puffer zurück. <br />Das Puffergrößen Argument gibt die Länge der Zeichenfolge "Server =" zurück, ohne abschließende Nullen.|  
  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Express LocalDB-Header und Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  
