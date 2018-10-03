---
title: LocalDBStopTracing-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7aea3e8a28f8d272f513065c49e0e673997c747d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076762"
---
# <a name="localdbstoptracing-function"></a>LocalDBStopTracing-Funktion
  Deaktiviert die Ablaufverfolgung der API-Aufrufe für alle SQL Server Express LocalDB-Instanzen, die zum aktuellen Windows-Benutzer gehören.  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
  
  
