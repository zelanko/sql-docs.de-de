---
title: Erstellen der SQL Server-Änderungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b4b7fb5d79d24a3333e21a9b0e6f4c115e967ffa
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84923431"
---
# <a name="create-the-sql-server-change-database"></a>Erstellen der SQL Server-Änderungsdatenbank
  Wenn Sie den Assistenten für neue Instanzen starten, wird die Seite Create CDC Database geöffnet. Verwenden Sie die Seite Create CDC Database, um Informationen zur neuen CDC-Instanz bereitzustellen und eine neue Änderungsdatenbank zu erstellen.  
  
 Wenn Sie eine neue CDC-Datenbank erstellen, wird diese für SQL Server CDC aktiviert. Für diese Aktivierung ist eine Anmeldung durch einen Benutzer erforderlich, der Mitglied der festen Serverrolle `sysadmin` ist.  
  
 Wenn ein Benutzer, der den Assistenten zum Erstellen einer Oracle CDC-Instanz startet, kein Mitglied der festen Serverrolle `sysadmin` ist, wird das Dialogfeld Verbindung mit SQL Server herstellen geöffnet. Darin werden die Anmeldeinformationen für ein Mitglied der Rolle sysadmin angefordert, damit der Task Enable the database for SQL Server CDC ausgeführt werden kann. Wenn die CDC-Datenbank erstellt wird, wird die `sysadmin` -Anmeldung verworfen, und der Vorgang wird mit der ursprünglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung fortgesetzt, die beim Zugreifen auf die Oracle Designer Console verwendet wurde.  
  
> [!IMPORTANT]  
>  Für andere Tasks als „Datenbank für SQL Server CDC aktivieren“ muss die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung, die zum Ausführen des Assistenten für neue Instanzen verwendet wird, über die feste Serverrolle `dbcreator` und die UPDATE-Berechtigungen für die MSXDBCDC-Datenbank verfügen.  
  
 Informationen zum Eingeben der Daten im Dialogfeld Verbindung mit SQL Server herstellen finden Sie unter [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).  
  
## <a name="options"></a>Tastatur  
 **Oracle CDC-Instanz**  
 Geben Sie die folgenden Informationen zur CDC-Instanz an, die Sie erstellen.  
  
-   **Name**: Geben Sie einen Namen für den neuen Dienst ein. Dieser Name wird auch als Name der neuen Änderungsdatenbank verwendet.  
  
-   **Beschreibung**: Geben Sie eine Beschreibung für die neue Instanz ein, um sie besser identifizieren zu können. Diese Eingabe ist optional.  
  
 **SQL Server Change Database**  
 Dieser Abschnitt wird verwendet, um die Datenbank zu erstellen.  
  
1.  **Change Database**: Der Name der neuen Änderungsdatenbank. Der Name der Datenbank entspricht dem Namen, den Sie der Instanz gegeben haben. In diesem schreibgeschützten Feld wird der vollständige Pfad zur Datenbank angezeigt.  
  
2.  **Datenbank erstellen**: Klicken Sie auf **Datenbank erstellen** , um die Datenbank zu erstellen.  
  
     Zum Erstellen der Datenbank muss die Anmeldung über die Serverrolle `sysasmin` verfügen. Weitere Informationen finden Sie oben unter dem Sicherheitshinweis.  
  
     Nachdem Sie die Datenbank erstellt haben, können Sie auf **Weiter** klicken, um den Schritt [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md)auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](how-to-create-the-sql-server-change-database-instance.md)   
 [Oracle CDC Service](the-oracle-cdc-service.md)  
  
  
