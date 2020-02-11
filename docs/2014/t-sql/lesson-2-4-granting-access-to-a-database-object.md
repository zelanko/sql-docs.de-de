---
title: Gewähren von Zugriff auf ein Datenbankobjekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 19381b0c5dbe690a60b2c536a8da759205c08c31
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643452"
---
# <a name="granting-access-to-a-database-object"></a>Erteilen des Zugriffs auf ein Datenbankobjekt
  Als Administrator können Sie die SELECT-Anweisungen aus der Tabelle **Products** und der **vw_Names** anzeigen und die **pr_Names** Prozedur ausführen. Mary kann jedoch nicht. Verwenden Sie die GRANT-Anweisung, um Mary die erforderlichen Berechtigungen zu erteilen.  
  
### <a name="procedure-title"></a>Titel der Prozedur  
  
1.  Führen Sie die folgende Anweisung aus, um `Mary` die `EXECUTE` -Berechtigung für die gespeicherte Prozedur `pr_Names` zu erteilen.  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 In diesem Szenario kann Mary mithilfe der gespeicherten Prozedur nur auf die **Products** -Tabelle zugreifen. Wenn Sie möchten, dass Mary eine SELECT-Anweisung für die Sicht ausführen kann, müssen Sie auch `GRANT SELECT ON vw_Names TO Mary`ausführen. Verwenden Sie die REVOKE-Anweisung, um den Zugriff auf Datenbankobjekte zu entfernen.  
  
> [!NOTE]  
>  Wenn der Besitzer der Tabelle, Sicht und gespeicherten Prozedur nicht das gleiche Schema ist, wird die Erteilung von Berechtigungen komplexer.  
  
## <a name="about-grant"></a>Informationen zu GRANT  
 Sie müssen über die EXECUTE-Berechtigung verfügen, um eine gespeicherte Prozedur auszuführen. Sie müssen über die SELECT-, INSERT-, UPDATE- und DELETE-Berechtigungen verfügen, um auf Daten zuzugreifen und sie zu ändern. Die GRANT-Anweisung wird auch für andere Berechtigungen wie die zum Erstellen von Tabellen verwendet.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zusammenfassung: Konfigurieren von Berechtigungen für Datenbankobjekte](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)  
  
  
