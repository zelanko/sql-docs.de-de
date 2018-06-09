---
title: Aktivieren oder Deaktivieren von R-Paket Remoteverwaltung für SQL Server-Machine Learning | Microsoft Docs
description: Aktivieren der R-Paket Remoteverwaltung auf SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 997db094cb5e69e0cbf82d9a7e247cb13ec1d452
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707658"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Aktivieren Sie oder deaktivieren Sie der remote-paketverwaltung für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt das Aktivieren der Remoteverwaltung der R-Pakete von einer Clientarbeitsstation oder einem anderen Machine Learning-Server. Nachdem das Paket-Feature in SQL Server aktiviert wurde, können Sie "revoscaler"-Befehle auf einem Client verwenden, um Pakete auf SQL Server installieren.

> [!NOTE]
> Derzeit wird die Verwaltung von R-Bibliotheken unterstützt. Unterstützung für Python geplant ist.

Standardmäßig wird die Verwaltungsfunktion externe Paket für SQL Server deaktiviert. Sie müssen ein separates Skript, um die Funktion zu aktivieren, wie im nächsten Abschnitt beschrieben ausführen.

## <a name="overview-of-process-and-tools"></a>Übersicht über Prozess- und tools

Verwenden Sie zum Aktivieren oder Deaktivieren der paketverwaltung auf SQL Server, die Befehlszeile-Hilfsprogramm **RegisterRExt.exe**, ist die im Lieferumfang der **"revoscaler"** Paket.

[Aktivieren der](#bkmk_enable) diese Funktion ist ein zweistufiger Prozess, einen Datenbankadministrator muss dann: Sie paketverwaltung auf SQL Server-Instanz (einmal pro SQL Server-Instanz) zu aktivieren, und klicken Sie dann aktivieren paketverwaltung für die SQL-Datenbank (einmal pro SQL Server -Datenbank).

[Deaktivieren von](#bkmk_disable) die Paket-Verwaltungsfunktion sind auch Multipel Schritte erforderlich: Sie Pakete auf Datenbankebene und Berechtigungen (eine pro Datenbank) zu entfernen, und entfernen Sie die Rollen vom Server (einmal pro Instanz).

## <a name="bkmk_enable"></a> Aktivieren Sie die paketverwaltung

1. Öffnen Sie auf SQL Server ein Eingabeaufforderungsfenster mit erhöhten Rechten, und navigieren Sie zu dem Ordner mit dem Hilfsprogramm RegisterRExt.exe. Der Standardspeicherort ist `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Führen Sie den folgenden Befehl, der entsprechenden Argumente für Ihre Umgebung bereitstellen:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl erstellt die Objekte auf Instanzebene auf dem SQL Server-Computer, die für die paketverwaltung erforderlich sind. Er startet auch des LaunchPads für die Instanz neu.

    Wenn Sie keine Instanz angeben, wird die Standardinstanz verwendet. Wenn Sie keinen Benutzer angeben, wird der aktuelle Sicherheitskontext verwendet. So ermöglicht z. B. der folgende Befehl paketverwaltung für die Instanz im Pfad RegisterRExt.exe, mit den Anmeldeinformationen des Benutzers, der die Eingabeaufforderung geöffnet:

    `REgisterRExt.exe /installpkgmgmt`

3. Um eine bestimmte Datenbank paketverwaltung hinzugefügt haben, führen Sie den folgenden Befehl von einer Eingabeaufforderung mit erhöhten Rechten aus:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Dieser Befehl erstellt eine Datenbank-Elementen, z. B. die folgenden Datenbankrollen, die zum Steuern von Benutzerberechtigungen verwendet werden: `rpkgs-users`, `rpkgs-private`, und `rpkgs-shared`.

    Aktivieren Sie der folgende Befehl beispielsweise paketverwaltung in der Datenbank, auf die Instanz, die dem RegisterRExt ausgeführt wird. Wenn Sie keinen Benutzer angeben, wird der aktuelle Sicherheitskontext verwendet.

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

4. Wiederholen Sie den Befehl für jede Datenbank, in dem Pakete installiert werden muss.

5. Um sicherzustellen, dass die neuen Rollen erfolgreich erstellt wurden, klicken Sie in SQL Server Management Studio auf die Datenbank, erweitern Sie **Sicherheit**, und erweitern Sie **Datenbankrollen**.

    Sie können auch eine Abfrage auf Sys. database_principals, z. B. Folgendes ausführen:

    ```SQL
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

Nachdem Sie diese Funktion aktiviert haben, können Sie "revoscaler"-Funktion zu installieren oder Deinstallieren von Paketen von einem Remoteclient von R verwenden.

## <a name="bkmk_disable"></a> Deaktivieren der paketverwaltung

1. Eine Eingabeaufforderung mit erhöhten Rechten führen Sie das Dienstprogramm RegisterRExt erneut aus, und deaktivieren Sie paketverwaltung auf Datenbankebene:

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl entfernt die Datenbankobjekte, die im Zusammenhang mit paketverwaltung aus der angegebenen Datenbank. Es entfernt auch alle Pakete, die von der gesicherten Speicherort im Dateisystem auf dem SQL Server-Computer installiert wurden.

2. Wiederholen Sie diesen Befehl für jede Datenbank, in denen paketverwaltung verwendet wurde.

3.  (Optional) Nachdem alle Datenbanken von Paketen, die mit dem vorherigen Schritt gelöscht haben, führen Sie den folgenden Befehl von einer Eingabeaufforderung mit erhöhten Rechten aus:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl entfernt die Paket-Verwaltungsfunktion aus der Instanz an. Sie müssen möglicherweise einmal, um Änderungen finden Sie unter den Launchpad-Dienst manuell neu zu starten.

## <a name="next-steps"></a>Nächste Schritte

+ [Verwenden Sie "revoscaler", um neue R-Pakete installieren](use-revoscaler-to-manage-r-packages.md)
+ [Tipps für die Installation von R-Pakete](packages-installed-in-user-libraries.md)
+ [Standardpakete](installing-and-managing-r-packages.md)