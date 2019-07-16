---
title: Zugriff auf Daten für DQS-Vorgänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 846eec4cb8ac678b5636bc436acce62dc7e2ecf7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935237"
---
# <a name="access-data-for-the-dqs-operations"></a>Zugriff auf Daten für DQS-Vorgänge

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Sie haben die folgenden Möglichkeiten, um die Quelldaten für [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS)-Vorgänge zu verwenden und die verarbeiteten Daten zu exportieren:  
  
-   Kopieren Sie die Quelldaten in eine Tabelle/Sicht in der DQS_STAGING_DATA-Datenbank, und verwenden Sie sie dann für DQS-Vorgänge. Sie können die verarbeiteten Daten auch in eine neue Tabelle in der DQS_STAGING_DATA-Datenbank exportieren. Hierzu muss dem Windows-Benutzerkonto Lese-/Schreibzugriff auf die Datenbank DQS_STAGING_DATA gewährt werden.  
  
-   Verwenden Sie die eigene Datenbank als Datenquelle für die DQS-Vorgänge und als Ziel zum Exportieren der verarbeiteten Daten. Stellen Sie deswegen sicher, dass sich die Datenbank in der gleichen SQL Server-Instanz wie die Data Quality Server-Datenbanken befindet. Andernfalls steht die Datenbank nicht für DQS-Vorgänge im Data Quality-Client zur Verfügung. Außerdem muss dem Windows-Benutzerkonto Zugriff auf die Datenbank DQS_STAGING_DATA zum Exportieren der Abgleichsergebnisse gewährt werden, da der Export der Abgleichsergebnisse ein zweiphasiger Prozess ist: zuerst werden die Abgleichsergebnisse in die temporären Tabellen in der Datenbank DQS_STAGING_DATA exportiert und dann in die Tabelle in der Zieldatenbank verschoben.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
  
-   Sie müssen die Installation des [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] durch Ausführen der Datei DQSInstaller.exe abgeschlossen haben. Weitere Informationen finden Sie unter [Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   Das Windows-Benutzerkonto muss ein Element der entsprechenden festen Serverrolle (z. B. securityadmin, serveradmin oder sysadmin) in der Datenbank-Engine-Instanz sein, um Zugriff auf die SQL-Anmeldung in Datenbanken zu gewähren/zu ändern.  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqsstagingdata-database"></a>So gewähren Sie einem Benutzer Lese-/Schreibzugriff auf die DQS_STAGING_DATA-Datenbank  
  
1.  Starten Sie Microsoft SQL Server Management Studio.  
  
2.  Erweitern Sie in Microsoft SQL Server Management Studio die SQL Server-Instanz, und erweitern Sie anschließend **Sicherheit**und **Anmeldungen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine SQL-Anmeldung, und klicken Sie auf **Eigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Anmeldungseigenschaften** auf die Seite **Benutzerzuordnung** im linken Bereich.  
  
5.  Aktivieren Sie im rechten Bereich in der Spalte **Map** (Zuordnung) das Kontrollkästchen für die **DQS_STAGING_DATA**-Datenbank, und wählen Sie anschließend im Bereich **Mitgliedschaft in Datenbankrolle für: DQS_STAGING_DATA** die folgenden Rollen aus:  
  
    -   **db_datareader**: Daten aus Tabellen/Ansichten lesen.  
  
    -   **db_datawriter**: Daten in Tabellen hinzufügen, löschen oder ändern.  
  
    -   **db_ddladmin**: Tabellen/Ansichten, erstellen, anpassen oder löschen.  
  
6.  Klicken Sie im Dialogfeld **Anmeldungseigenschaften** auf **OK** , um die Änderungen zu übernehmen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Versuchen Sie, DQS-Vorgänge auszuführen, die auf die Datenbank als Datenquelle für den DQS-Vorgang zugreifen, und exportieren Sie dann die verarbeiteten Daten in die Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)  
  
  
