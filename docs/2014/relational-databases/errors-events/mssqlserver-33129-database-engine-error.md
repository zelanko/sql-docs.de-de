---
title: MSSQLSERVER_33129 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 991757d1bfeae8ecc0dec3a69d82c3dcab6415b1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531652"
---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33129|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CANNOT_DISABLE_WIN_GROUP|  
|Meldungstext|Kann ALTER_LOGIN mit dem DISABLE-Argument nicht dazu verwenden, den Zugriff auf eine Windows-Gruppe zu verweigern.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung wird angezeigt, wenn Sie versuchen, den Anmeldenamen einer Windows-Gruppe zu deaktivieren.  
  
## <a name="user-action"></a>Benutzeraktion  
 Der Anmeldename einer Windows-Gruppe kann nicht deaktiviert werden. Um die Zugriffsberechtigung einer Windows-Gruppe vorübergehend zu entfernen, heben Sie die CONNECT-Berechtigung des Anmeldenamens für die Windows-Gruppe mit REVOKE auf. Windows-Benutzer haben möglicherweise weiterhin über ihren individuellen Anmeldenamen oder eine andere Windows-Gruppe Zugriff. Im folgenden Beispiel wird die Verbindungsberechtigung für die Gruppe "Accounting" der Domäne WESTCOAST aufgehoben.  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
