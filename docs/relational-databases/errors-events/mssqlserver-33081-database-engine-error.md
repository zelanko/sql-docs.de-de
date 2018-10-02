---
title: MSSQLSERVER_33081 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3bb040a3e43d9cc7e3702037900f1474cde5013c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795558"
---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33081|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Meldungstext|Fehler beim Laden des Kryptografieanbieters ‚%.*ls’ aufgrund einer ungültigen Authenticode-Signatur oder eines ungültigen Dateipfades.  Überprüfen Sie vorhergehende Meldungen auf weitere Fehler.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte den in der Fehlermeldung aufgeführten Kryptografieanbieter nicht laden. Es sind mehrere Win API-Fehler aufgetreten, die diesen Fehler möglicherweise verursachen. Der Ringpuffer enthält den Namen der fehlerhaften API und den von der API zurückgegebenen Windows-Fehlercode. Weitere Informationen erhalten Sie, indem Sie die folgende Abfrage der sys.dm_os_ring_buffers-Sicht ausgeben.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Benutzeraktion  
Suchen Sie den Windows-Fehlercode in MSDN (http://msdn.microsoft.com/)), um das Problem zu analysieren. Beheben Sie den Fehler, oder wenden Sie sich an [!INCLUDE[msCoName](../../includes/msconame-md.md)]-CSS für weitere Informationen. Wenn Sie CSS in Anspruch nehmen möchten, halten Sie bitte die folgenden Informationen für unsere Supportmitarbeiter bereit.  
  
-   Das Fehlerprotokoll, das die Meldung über den Fehler beim Laden des Kryptografieanbieters beinhaltet.  
  
-   Die Ausgabe der folgenden Anweisung:  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> Versuchen Sie, die Ringpufferinformationen möglichst umgehend zu erfassen, da Ringpufferinformationen während eines Neustarts verloren gehen können.  
  
