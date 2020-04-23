---
title: Informationen zu den Codebeispielen in der Dokumentation
description: Es gibt einige Punkte zu beachten, wenn Sie die Codebeispiele in der Dokumentation zu Microsoft-Treibern für PHP für SQL Server ausführen.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c90f2f1a420f1ab40f99a2fe83c928890e37e621
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631891"
---
# <a name="about-code-examples-in-the-documentation"></a>Informationen zu den Codebeispielen in der Dokumentation
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>Hinweise zu den Codebeispielen
Es gibt einige Punkte zu beachten, wenn Sie die Codebeispiele in der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] -Dokumentation ausführen:  
  
-   In fast allen Beispielen wird davon ausgegangen, dass SQL Server 2008 oder höher und die AdventureWorks-Datenbank auf dem lokalen Computer installiert sind.  
  
    Informationen zur Vorgehensweise beim Herunterladen der kostenlosen Editionen und Testversionen von SQL Server finden Sie unter [SQL Server](https://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Weitere Informationen zum Herunterladen und Installieren der AdventureWorks-Datenbank finden Sie auf der [AdventureWorks-Seite im Repository mit SQL Server-Beispielen auf GitHub](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works).
  
-   Fast alle Codebeispiele in dieser Dokumentation sollen über die Befehlszeile ausgeführt werden, die das automatische Testen aller Codebeispiele ermöglicht. Informationen über das Ausführen von PHP über die Befehlszeile finden Sie unter [PHP über die Befehlszeile](https://php.net/manual/en/features.commandline.php).  
  
-   Obwohl Beispiele dafür vorgesehen sind, von der Befehlszeile ausgeführt zu werden, kann jedes Beispiel auch ausgeführt werden, indem Sie es in einem Browser aufrufen, ohne Änderungen am Skript vorzunehmen. Für eine schöne Formatierung der Ausgabe ersetzen Sie in jedem Beispiel jedes „\n“ durch „\<\/br>“, bevor Sie es in einem Browser aufrufen.  
  
-   Um jedes Beispiel auf das Wesentliche zu beschränken, wird die richtige Fehlerbehandlung nicht in allen Beispielen durchgeführt. Es wird empfohlen, dass jeder Aufruf einer **sqlsrv** -Funktion oder PDO-Methode auf Fehler überprüft wird und gemäß den Anforderungen der Anwendung behandelt wird.  
  
    Eine einfache Möglichkeit, Fehlerinformationen abzurufen, wenn ein Fehler aufgetreten ist, ist das Beenden des Skripts mit der folgenden Codezeile:  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    Oder falls Sie PDO verwenden,  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    Weitere Informationen zum Behandeln von Fehlern und Warnungen finden Sie unter [Handhabung von Fehlern und Warnungen](handling-errors-and-warnings.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Overview of the Microsoft Drivers for PHP for SQL Server (Übersicht über die Microsoft-Treiber für PHP für SQL Server)](overview-of-the-php-sql-driver.md)
  
