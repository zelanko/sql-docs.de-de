---
title: Localdbgetinhaltungen-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 92aa65bd2d3aad71f2467efaa7a09f75f20d8f63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032251"
---
# <a name="localdbgetinstances-function"></a>LocalDBGetInstances-Funktion
  Gibt alle SQL Server Express LocalDB-Instanzen mit der angegebenen Version zurück.  
  
 **Header Datei:** sqlncli. h  
  
## <a name="syntax"></a>Syntax  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a>Parameter  
 *pInstanceNames*  
 Ausgeben Wenn diese Funktion zurückgegeben wird, enthält Sie die Namen der benannten und der localdb-Standard Instanzen auf der Arbeitsstation des Benutzers.  
  
 *lpdwnumofinhaltungen*  
 [Eingabe/Ausgabe] Bei Eingabe enthält dieses Objekt die Anzahl der Slots für Instanznamen im *pInstanceNames* -Puffer. Enthält bei Ausgabe die Anzahl der localdb-Instanzen, die auf der Arbeitsstation des Benutzers gefunden wurden.  
  
## <a name="returns"></a>Rückgabe  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Der Eingabepuffer ist zu kurz. Abschneiden wurde nicht angefordert.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Der Pfad, unter dem die Instanz gespeichert werden soll, ist länger als MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Auf eine Instanzregistrierung kann nicht zugegriffen werden.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Eine Instanzkonfiguration ist beschädigt.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Express LocalDB-Header und Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  
