---
title: Aktivieren oder Deaktivieren der Remote-R-Paketverwaltung
description: Aktivieren der Remote-r-Paketverwaltung auf SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (in-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 9cc08b1227751559ea509838fe8fc3a446296770
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470022"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Aktivieren oder Deaktivieren der Remote Paketverwaltung für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie die Remote Verwaltung von R-Paketen über eine Client Arbeitsstation oder eine andere Machine Learning Server aktivieren. Nachdem die Paket Verwaltungsfunktion auf SQL Server aktiviert wurde, können Sie mithilfe von revoscaler-Befehlen auf einem Client Pakete auf SQL Server installieren.

> [!NOTE]
> Derzeit wird die Verwaltung von R-Bibliotheken unterstützt. Unterstützung für python finden Sie in der Roadmap.

Standardmäßig ist das Feature für die externe Paketverwaltung für SQL Server deaktiviert. Sie müssen ein separates Skript ausführen, um das Feature zu aktivieren, wie im nächsten Abschnitt beschrieben.

## <a name="overview-of-process-and-tools"></a>Übersicht über den Prozess und die Tools

Verwenden Sie zum Aktivieren oder Deaktivieren der Paketverwaltung auf SQL Server das Befehlszeilen Dienstprogramm **registerrext. exe**, das im **revoscaler** -Paket enthalten ist.

[Das Aktivieren](#bkmk_enable) dieses Features ist ein zweistufiger Prozess, bei dem ein Datenbankadministrator erforderlich ist: Sie können die Paketverwaltung auf der SQL Server Instanz (einmal pro SQL Server Instanz) aktivieren und dann die Paketverwaltung für die SQL-Datenbank aktivieren (einmal pro SQL Server Datenbank). ).

Das [Deaktivieren](#bkmk_disable) des Paket Verwaltungs Features erfordert auch multipel-Schritte: Sie entfernen Pakete und Berechtigungen auf Datenbankebene (einmal pro Datenbank) und entfernen dann die Rollen vom Server (einmal pro Instanz).

## <a name="bkmk_enable"></a>Paketverwaltung aktivieren

1. Öffnen Sie auf SQL Server eine Eingabeaufforderung mit erhöhten Rechten, und navigieren Sie zu dem Ordner, der das Hilfsprogramm registerrext. exe enthält. Der Standard Speicherort `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`ist.

2. Führen Sie den folgenden Befehl aus, um die entsprechenden Argumente für Ihre Umgebung bereitzustellen:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Mit diesem Befehl werden Objekte auf Instanzebene auf dem SQL Server Computer erstellt, die für die Paketverwaltung erforderlich sind. Außerdem wird das Launchpad für die-Instanz neu gestartet.

    Wenn Sie keine Instanz angeben, wird die Standard Instanz verwendet. Wenn Sie keinen Benutzer angeben, wird der aktuelle Sicherheitskontext verwendet. Der folgende Befehl aktiviert z. b. die Paketverwaltung auf der-Instanz im Pfad von registerrext. exe unter Verwendung der Anmelde Informationen des Benutzers, der die Eingabeaufforderung geöffnet hat:

    `REgisterRExt.exe /install pkgmgmt`

3. Führen Sie den folgenden Befehl an einer Eingabeaufforderung mit erhöhten Rechten aus, um eine Paketverwaltung zu einer bestimmten Datenbank hinzuzufügen:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Mit diesem Befehl werden einige Daten Bank Artefakte erstellt, einschließlich der folgenden Daten bankrollen, die zum Steuern `rpkgs-users`von `rpkgs-private`Benutzerberechtigungen `rpkgs-shared`verwendet werden:, und.

    Der folgende Befehl aktiviert z. b. die Paketverwaltung in der-Datenbank auf der-Instanz, in der registerrext ausgeführt wird. Wenn Sie keinen Benutzer angeben, wird der aktuelle Sicherheitskontext verwendet.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Wiederholen Sie den Befehl für jede Datenbank, in der Pakete installiert werden müssen.

5. Um zu überprüfen, ob die neuen Rollen erfolgreich erstellt wurden, klicken Sie in SQL Server Management Studio auf die Datenbank, erweitern Sie **Sicherheit**, und erweitern Sie **Daten bankrollen**.

    Sie können auch eine Abfrage für sys. database_principals ausführen, wie z. b. Folgendes:

    ```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

Nachdem Sie diese Funktion aktiviert haben, können Sie die Funktion "revoscaler" verwenden, um Pakete von einem Remote-R-Client zu installieren oder zu deinstallieren.

## <a name="bkmk_disable"></a>Paketverwaltung deaktivieren

1. Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten das Hilfsprogramm registerrext erneut aus, und deaktivieren Sie die Paketverwaltung auf Datenbankebene:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl entfernt Datenbankobjekte, die sich auf die Paketverwaltung beziehen, aus der angegebenen Datenbank. Außerdem werden alle Pakete entfernt, die aus dem gesicherten Dateisystem Speicherort auf dem SQL Server Computer installiert wurden.

2. Wiederholen Sie diesen Befehl für jede Datenbank, in der die Paketverwaltung verwendet wurde.

3.  Optionale Nachdem alle Datenbanken mithilfe des vorherigen Schritts aus Paketen gelöscht wurden, führen Sie den folgenden Befehl an einer Eingabeaufforderung mit erhöhten Rechten aus:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Mit diesem Befehl wird das Paket Verwaltungs Feature aus der-Instanz entfernt. Möglicherweise müssen Sie den Launchpad-Dienst erneut manuell neu starten, um die Änderungen anzuzeigen.

## <a name="next-steps"></a>Nächste Schritte

+ [Verwenden von revoscaler zum Installieren neuer R-Pakete](use-revoscaler-to-manage-r-packages.md)
+ [Tipps zum Installieren von R-Paketen](packages-installed-in-user-libraries.md)
+ [Standardpakete](../package-management/default-packages.md)
